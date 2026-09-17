Event feed
==========

The event feed is a resumable, account-wide notification feed for responsive
integrations — **not an audit log, and not guaranteed delivery**. It pairs a
live push stream (a wake-up signal over WebSocket) with catch-up polling
(best-effort recovery of anything push missed, with a measured bound).
Consumers should treat both lanes as notifications: deduplicate by event id
(inbox items by `addressing_id`, since one event can address you for several
reasons), and **refetch the referenced resource before acting on it**.

The contract:

- Live messages may be delayed, duplicated, or dropped; polling repairs missed
  live delivery for events **with ids above your position** whose transactions
  commit within a bounded safety delay (about 30 seconds). The bound is
  defined relative to your position, not wall-clock: entering at the present
  places everything already visible — and any still-uncommitted event that
  drew an earlier id — behind your entry position for good (see
  [Poll events](#poll-events)). The bound is measured server-side, but it is
  not absolute: an unusually long-running transaction, or an event deleted
  before it ever became poll-visible, can be missed entirely. Workflows that
  need completeness must corroborate against the canonical resource APIs
  rather than lean on the feed.
- Feed membership is fixed when an event is created; authorization is
  evaluated when you read. Revoking someone's Basecamp access takes effect
  immediately once the revocation commits (live streams are disconnected);
  newly granted access shows up in polls immediately — including re-polls of
  older positions — but requires reconnecting the live stream, since its
  access set is built at subscribe.
- OAuth deauthorization is looser: it does not disconnect an already-open
  live stream, and short-lived server-side authentication caching plus the
  stream-ticket lifetime mean a deauthorized client's polls and freshly
  minted tickets can keep working for a few minutes before going dark. That
  grace window is best-effort and unpinned — it emerges from cache and
  ticket lifetimes rather than a tested contract, so don't build on its
  exact duration.
- Only cataloged event types are served (see [Event types](#event-types)).
  Draft publication is delivered as the corresponding `.created` type.
- The catalog grows, and it grows under you: a poll or subscription with no
  `types` filter is asking for the whole catalog, so new types start arriving
  on the deploy that adds them, with no opt-in. Name the types you handle if
  that matters to you.
- Workshop and not-yet-open spaces never feed: activity in project templates,
  the template library, playground projects, and drafted or importing
  projects is excluded at creation. Content constructed *by* machinery —
  template application, recurring to-do generation — never feeds either;
  the feed carries what people (and agents) do, not what construction
  produces. Copies aren't served: a copied to-do or card arrives with its
  history replayed silently and no event of its own. Moves between projects
  are: a to-do or card moved in from another project is new activity there,
  delivered as `todo.created` or `card.created`. Moves within a project are
  served as `todo.moved` and `card.moved` — a to-do to another list or
  group, a card to another column or on or off hold — as thin pointers,
  with `card.moved` naming the columns in `details`. Copying a list or
  card *out of a template* builds fresh to-dos and cards, so those are
  served as ordinary creations. Circles (direct-message spaces) do feed.
- Positions are scoped to your account and filter set. Persist a position only
  after you have accepted the events preceding it.
- The feed starts at a fixed epoch, an operational fence that can be raised
  (for example, after a database rollback leaves an interval of history
  unmarked for the feed). Requests below the epoch receive `410 Gone` with the
  epoch and a `resume` URL that re-enters at the epoch with your filters
  preserved, so the servable history above the fence is not skipped. History from before the feed shipped is never backfilled:
  `since=0` replays served history only, back to the epoch, not the
  account's whole past.

Endpoints:

- [Poll events](#poll-events)
- [Poll the inbox](#poll-the-inbox)
- [Create a stream ticket](#create-a-stream-ticket)

Event types
-----------

The feed serves a curated catalog of event types. Filter with the `types`
parameter (comma-separated). Currently:

| Type | Fires when |
| --- | --- |
| `comment.created` | A comment is posted |
| `comment.content_changed` | A comment's body is edited |
| `message.created` | A message is posted or published from a draft |
| `message.content_changed` | A message's body is edited |
| `message.subject_changed` | A message's subject is edited |
| `todo.created` | A to-do is added, published, or moved in from another project |
| `todo.completed` | A to-do is completed |
| `todo.moved` | A to-do moves to another list, or to another group within its list |
| `todo.content_changed` | A to-do's name is edited |
| `todo.description_changed` | A to-do's notes are edited |
| `todo.scheduled` | A to-do gains a due or start date |
| `todo.rescheduled` | A dated to-do's due or start date moves |
| `todo.unscheduled` | A to-do's dates are cleared |
| `todo.assignment_changed` | A to-do's assignees change |
| `card.created` | A card table card is added or moved in from another project |
| `card.completed` | A card is completed |
| `card.moved` | A card moves to another column, or on or off hold; `details` carries `column_id` and `previous_column_id`, the containing columns (going on hold within a column reports the same column twice) |
| `card.content_changed` | A card's body is edited |
| `card.title_changed` | A card's title is edited |
| `card.due_on_changed` | A card's due date is set, moved, or cleared |
| `card.assignment_changed` | A card's assignees change |
| `chat.line.created` | A Campfire line is posted: text, rich text, code, upload, or integration lines (sound-command "plays" are excluded) |
| `boost.created` | Someone boosts a recording or an event on it (a to-do completion, say). `recording_id` is the recording either way; `details` carries `boost_id`, plus `boosted_event_id` and its `boosted_event_type` when the boost landed on an event (both null for a boost on the recording itself — the event's boosts are listed under the event, not the recording; `boosted_event_type` is also null when the boosted event's kind isn't cataloged). Removing a boost emits nothing. Boosts stay out of the legacy per-project webhooks; this feed and the inbox are their surface |
| `question.created` | An automatic check-in question is created |
| `question.answer.created` | Someone answers a check-in question |

Edits are served so you can hear an instruction added to something already
posted, wherever the person put it — note that a to-do's `content` is its
name and its notes are its `description`. A save fires one event per field
changed, so editing a message's subject and its body together serves two
events, and repeated saves each fire their own — refetch the recording and
deduplicate on what you read, not on the number of events. A to-do's dates
are the exception: they move together under one scheduling event, so
dragging a spanned to-do serves one, not two.

Dates move under different types on the two sides, because Basecamp records
them differently and the catalog exposes that rather than inventing a type
over it. A card's due date is a plain field: set, moved and cleared all arrive
as `card.due_on_changed`. A to-do's dates go through scheduling, which covers
its start date as well as its due date, and split three ways —
`todo.scheduled` when a to-do that had no dates gains one, `todo.rescheduled`
when a dated one moves, `todo.unscheduled` when they are cleared. Hearing every
date move on a to-do or a card means subscribing to all four. Dates elsewhere
are not served: not on a subtask, not on an event in the schedule, and not a
to-do's repetition schedule, which is a rule for making future to-dos rather
than a date on this one.

Of the types above, one edit is missing: a comment's title. A comment has
one, but nobody writes it — it is derived from whatever the comment is on,
and the kind fires when that derivation catches up, usually on the comment's
next real edit, which is served under its own type.

Serving edits added nothing outside the feed: an edit has never appeared in a
project's timeline or activity, and raises no notification of its own. The
exception is `todo.scheduled` and `todo.rescheduled`, which have notified a
to-do's assignees since long before the feed existed and still do; nothing
about that changed when they were cataloged.

Editing to add a mention still notifies the person mentioned, as it always
has — that is the mention system, not this event. It reads the fields carrying
rich text, so a body or a to-do's notes reach the person named while a card's
title or a message's subject don't. The exception is a to-do with no notes,
where an `@callsign` in its name is read instead.

Integration lines mean agents hear bots — and themselves. Deduplicate or
ignore your own creator id if you both post and listen.

Pings (direct-message Campfires) ride `chat.line.created` like any other
chat line — there is no separate ping type. Filter on the Circle's bucket
id if you only want (or want to avoid) direct messages.

The catalog grows as consumers need more types — ask! Catalog membership is
evaluated at read: if a type is ever removed, its history disappears from
polls too, rather than surviving as a frozen archive — and a `types` filter
that still names the removed type is rejected as an unknown type (the filter
`400`) until you drop it, which changes your filter set, so re-enter with
`since=` rather than resuming the held position. Additions cut the
other way — a newly cataloged type's history becomes servable back through
`since=0` replays, but a held position that already advanced past those
events never revisits them.

Poll events
-----------

* `GET /events.json` will return a list of events since your last position,
  oldest first, in strict event-id order.

Parameters:

- With no `since` or `position`, the feed begins **at the present** —
  equivalent to `since=now`. Historical replay is explicit: pass `since`.
  Entering at the present sets your position to the newest visible event:
  events already committed, and any in-flight event whose transaction drew an
  earlier id and commits after your entry, fall behind that position and are
  never served to it — the delivery bound covers ids above your position
  only. Connect the live stream before entering (the recommended protocol) to
  hear in-flight stragglers; or enter via `since=<id>` from a known point.
- `since=<event_id>` — start after the given event id. `since=0` replays all
  served history back to the feed's epoch — under a raised epoch it enters at
  the epoch rather than 410ing. `since=now` skips history and starts at the present. Use
  `since` to enter the feed, to recover from an invalid position, or to
  acknowledge a filter change.
- `position=<token>` — resume from a position token issued by a previous
  response. Positions are signed and opaque.
- `types`, `buckets`, `creators` — optional comma-separated filters. `buckets`
  and `creators` accept at most 100 ids each; `types` accepts any subset of
  the catalog with no separate count cap. Raw filter input is bounded before
  parsing: array-form lists over 1,000 elements, or input over 16 KB in
  either form, are rejected with the filter `400` (comma-form lists are
  bounded by the byte cap and the id caps). Changing filters invalidates held positions (see below).
- `performers`, `exclude_performers` — filter by the **effective performer**:
  the agent that carried out a delegated action (`performed_by_id`), else the
  creator. At most 100 ids each; the literal `self` means the request's
  effective actor — the agent on a delegated (agent-linked) token, otherwise
  the authenticated person — and is resolved to that id server-side before
  filtering and digesting, so continuation URLs and digests carry the id,
  not the literal.
  **`exclude_performers=self` is the loop guard**: an agent that acts on what
  it hears should exclude its own performances rather than suppress all agent
  activity.
- `actor_types` — opt-in filter by actor kind: `agent`, `person`, or both.
  A delegated event's actor is the agent that performed it; a direct event's
  actor is its creator, typed by what it currently is (humans, integrations,
  and tombstones are `person`). This is a filter, not a default — agent
  activity is real account activity, and suppressing it wholesale breaks
  agent-to-agent workflows. Use `exclude_performers=self` to avoid echo.

Every successful response is an envelope — the body is the contract:

- `events` — up to 100 events, oldest first, in strict event-id order. Each
  event is a thin pointer — `id`, `kind`, `action`, `event_type`, `bucket_id`,
  `creator_id`, `performed_by_id`, `recording_id`, `created_at` — plus a
  `details` object only for types that publish one (`boost.created`, `card.moved`); refetch
  the referenced resource for anything else. Pages
  along a walk may be empty while it crosses history your filters exclude
  (the walk advances through bounded scan windows internally) — keep
  following `next`.
- `position` — a durable position token for resuming later. Persist it only
  after you've processed the page's events. Every `200` body carries
  `position`; error responses carry their own shapes.
- `next` — a continuation URL, present only while the current walk has more
  to serve; follow it to continue. When `next` is absent, this walk is done:
  poll again later from the durable position.

The `X-Feed-Position` and `Link: <...>; rel="next"` response headers echo
`position` and `next` as conveniences.

Precisely, `next` appears when a page proved more servable history remains: a
full page of events below the walk's head, or a whole scan window that was
entirely outside the safety delay with event ids still remaining below the
head. A walk terminates at the head **frozen when the walk started**, not the
live head — events created mid-walk belong to the next poll. And a page cut
short by the safety delay deliberately withholds `next`: poll again from
`position` once those young events age out of the delay.

Polls serve only events already outside a fixed safety delay, so they don't
skip events whose transactions are still committing — a measured bound, not a
guarantee (see the contract above). Events may therefore appear in polls up to
~30 seconds after they're pushed live; that's expected, so deduplicate by
event id.

Error responses:

- `400 Bad Request` — **branch on the body's `reason`, never on the wording of
  `error`**, which is prose and may be reworded. Two values, with opposite
  recoveries:

  `"invalid_position"` — a malformed **position** (including array-form
  `position`/`since` parameters, and a `since` outside the signed 64-bit id
  range). Recoverable: resume with `since=<event id>` or `since=now`. A
  position minted for a different account is indistinguishable from a
  malformed one and gets this same `400`.

  ```json
  {
    "error": "Unrecognized position. Resume with since=<id> or since=now.",
    "reason": "invalid_position"
  }
  ```

  `"invalid_filter"` — a malformed **filter** (unknown `types`, non-integer
  ids, more than 100 `buckets`/`creators` ids, oversized raw input, or a
  dimension this resource doesn't apply to). Not recoverable by a cursor reset:
  the error names the offending filter, so fix the filters.

  ```json
  {
    "error": "Unknown event types: nope.created. Fix the filters; a position reset won't help.",
    "reason": "invalid_filter"
  }
  ```

  **A `400` with no `reason` never reached the feed**, and neither recovery
  above applies — fix the request itself. These are raised before the feed
  gets the request and do not carry its error shape, so don't assume a `400`
  body is JSON at all, or that an `error` in one means what the two above
  mean:

  - a query string the server can't parse (invalid `%`-encoding, conflicting
    `a[b]`/`a[b][c]` shapes, excessive nesting) answers the framework's own
    `{"status": 400, "error": "Bad Request"}` when the request asks for JSON
    — by `Accept` or by the `.json` extension — and an empty body otherwise.
    Note that it reuses the `error` key for something unrelated;
  - a missing `User-Agent` answers `text/plain` with no JSON at all (see
    [Identifying your application](../README.md#identifying-your-application)).

  So: `reason` present, branch on it; `reason` absent, the request was
  malformed before the feed saw it.
- `409 Conflict` — the position was minted for a different filter set. The
  body names both sides: `position_digest` (the digest the position was
  minted for) and `filters_digest` (the digest of the filters this request
  presented). Re-enter with `since=` to acknowledge the filter change.
- `410 Gone` — the position predates the feed's epoch. The body carries
  `epoch_after_id` and a `resume` URL re-entering at the epoch with your
  canonical filters preserved.

###### Example JSON Response
<!-- START GET /events.json -->
```json
{
  "events": [
    {
      "id": 1071915468,
      "kind": "message_created",
      "action": "created",
      "created_at": "2026-07-14T06:10:00.159Z",
      "event_type": "message.created",
      "bucket_id": 2085958499,
      "creator_id": 1049715945,
      "performed_by_id": null,
      "recording_id": 1069479766
    }
  ],
  "position": "aBcD..."
}
```
<!-- END GET /events.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/events.json?since=now
```

Filter digests (srv2)
---------------------

Positions bind to their filter set through a versioned digest, published here
so SDKs can compute the server's canonical filter identity locally (for
checkpoint keys, and to interpret the `409` body):

1. Canonicalize each present dimension: `types`, `actor_types`, and
   `reasons` deduplicated and sorted bytewise (UTF-8);
   `buckets`/`creators`/`performers`/`exclude_performers` coerced to base-10
   integers, deduplicated **after** coercion (`1` and `01` are the same id),
   ascending — with the literal `self` resolved to the effective actor's id
   (the agent on a delegated request, otherwise the authenticated person)
   **before** digesting, so a position never means different filters for
   different people.
2. Build a JSON object keyed by dimension name — **present dimensions
   only**, keys sorted bytewise (`actor_types`, `buckets`, `creators`,
   `exclude_performers`, `performers`, `reasons`, `types`). The empty filter
   set is `{}`.
3. Serialize as minimal RFC 8259 JSON — no whitespace, no trailing newline.
4. Digest: SHA-256 of those bytes, first 16 lowercase hex characters
   (8 bytes).

Keying by name makes the scheme extension-stable: absent dimensions
contribute no bytes, so a newly introduced filter dimension never moves the
digest of any filter set that doesn't use it.

The wire format is the bare 16-hex string — exactly what `position_digest`
and `filters_digest` carry in the `409` body. `srv2` names this scheme
version for client-side lineage keys (`srv2-<digest>`); the server never
emits the prefix. Any change to the canonicalization or algorithm ships as
`srv3` with new vectors — the vectors below are stable:

| Input | Canonical JSON | Digest |
| --- | --- | --- |
| (no filters) | `{}` | `44136fa355b3678a` |
| `types=message.created` | `{"types":["message.created"]}` | `38b223c13c89dc89` |
| `types=todo.completed,message.created&buckets=2,1` | `{"buckets":[1,2],"types":["message.created","todo.completed"]}` | `90108e436c72bfd1` |
| `types=todo.completed,message.created&buckets=2,1&creators=9` | `{"buckets":[1,2],"creators":[9],"types":["message.created","todo.completed"]}` | `5d0b83594d8e5630` |
| `buckets=01` (also `buckets=1,01`) | `{"buckets":[1]}` | `e545e11ffb55966a` |
| `buckets=1,...,100` (the cap boundary) | `{"buckets":[1,2,...,100]}` | `e2acd9c77b72cd99` |
| `performers=9` (also `performers=self` when the effective actor is person 9) | `{"performers":[9]}` | `97c45ef5d7ed59c2` |
| `exclude_performers=9` | `{"exclude_performers":[9]}` | `e52acfcd22b34d9e` |
| `actor_types=agent` | `{"actor_types":["agent"]}` | `cfcc84d9873823db` |
| `reasons=mentioned` (inbox) | `{"reasons":["mentioned"]}` | `a68353156f17c45a` |
| `reasons=mentioned,assigned&performers=9&types=comment.created` | `{"performers":[9],"reasons":["assigned","mentioned"],"types":["comment.created"]}` | `99b78eea305639b8` |

srv2's domain is the cataloged type strings, the actor-type strings `agent`
and `person`, the addressing-reason strings (`mentioned`, `assigned`,
`subscribed`, `watched`, `boosted`, `pinged` -- the inbox's reasons table
below), and integer ids, nothing else. The literal `self` is resolved to an
id before digesting and never appears in canonical JSON. Quoted or
non-ASCII types are outside the valid domain: unknown types, actor types,
and reasons are rejected with the filter `400` before any digest is
computed, so no vector for them exists.

Poll the inbox
--------------

* `GET /inbox.json` will return the authenticated principal's **addressed
  items** — the low-noise "someone addressed you" lane, as its own resource
  rather than a filter over the account feed. **Agents only for now**: any
  other principal receives `403 Forbidden`. People join when subscriptions
  arrive.

An item is a first-class delivery with its own identity: the same event can
address one person for several reasons, and each reason is its own item.
Deduplicate items by `addressing_id`, never by event id — the feed's rule
would discard every reason but one. Reasons:

| Reason | You were… |
| --- | --- |
| `mentioned` | @mentioned in the content of a creation or publication, or newly @mentioned by an edit |
| `assigned` | assigned a to-do or card |
| `subscribed` | subscribed to the recording (or its container) the activity happened in |
| `watched` | watching a to-do list's additions or a card table column's cards, or a to-do's or card's completion |
| `pinged` | a participant in the Circle (Ping) the line was posted to |
| `boosted` | the person whose work was boosted |

An edit addresses only what it added. Each edit event names the attribute it
changed — `message.content_changed` the body, `message.subject_changed` the
subject — and reads that attribute on both the new version and the one it
replaced, addressing the difference. So editing a body to add a mention
addresses once, on the body's event, even when the same save also renamed the
recording and served a second event alongside it. Leaving a mention where it
already was addresses nobody again, and an edit that touches no mention —
moving a date, rewriting a title that names nobody — addresses nobody at all.
Publishing a draft that gained the mention in the same save addresses once,
never twice — on the publication where it read the mention, on the edit's own
event where it didn't.

Addressing is not the notification lane described further up, and the two
differ here. Addressing reads whatever text the named attribute holds, so an
`@callsign` typed into a message's subject or a card's title **does** address
you, and a to-do's name is read on its own terms rather than only when its
notes are blank. The one place that costs a second item: add the same mention
to two attributes in one save and each attribute's event addresses you — two
new mentions in two places, one item each.

Items are never self-addressed: your own actions (as creator or performing
agent) are echo, not address. Being addressed doesn't confer access — an item
whose event you can no longer read is dropped at read time, exactly as the
feed drops it.

Parameters: `since=0` replays the earliest items still retained (items are
kept for 30 days); `since=now` enters at the present; `position` resumes.
Filters: `reasons` (comma-separated, from the table above), plus `types` and
`buckets` as narrowing. Filter digests use the same srv2 scheme as the feed,
with `reasons` as its own dimension. Positions are bound to your account,
your person, and your filter set, and are never interchangeable with feed
positions.

The envelope: `items` (oldest first, in strict item-id order), `position`,
and `next` while a walk has more to serve; `X-Feed-Position` and
`Link: rel="next"` echo them. Errors follow the feed's contract, except that
`410 Gone` here means the position fell behind the retention window — the
`resume` URL re-enters at `since=0`, the earliest retained item: a stale
position has seen none of the retained backlog, so that entry is exactly-once
continuation.

###### Example JSON Response
<!-- START GET /inbox.json -->
```json
{
  "items": [
    {
      "addressing_id": 991,
      "reason": "mentioned",
      "addressed_at": "2026-07-14T06:10:00.159Z",
      "event": {
        "id": 1071915468,
        "kind": "comment_created",
        "action": "created",
        "created_at": "2026-07-14T06:10:00.159Z",
        "event_type": "comment.created",
        "bucket_id": 2085958499,
        "creator_id": 1049715945,
        "performed_by_id": null,
        "recording_id": 1069479766
      }
    }
  ],
  "position": "aBcD..."
}
```
<!-- END GET /inbox.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/inbox.json?since=0
```

Live delivery: subscribe to `EventsChannel` with `"inbox": true` (plus any
`reasons`/`types`/`buckets`) on a ticket connection to receive each item as
it's written, in the same shape as above. An inbox subscription replaces the
account streams for that connection rather than adding to them.

Agent-to-agent brakes: because two agents can address each other without
ever addressing themselves, inbox delivery carries brakes that self-exclusion
can't provide — a per-account delivery budget per minute, a circuit breaker
on runs of agent-performed deliveries (reset by the next human-performed
one), and an operator kill switch. A braked event is counted, not delivered;
if your agent goes quiet under a burst, that's why.

Create a stream ticket
----------------------

* `POST /events/stream_ticket.json` mints a short-lived signed ticket (about
  2 minutes) for opening a live event stream over WebSocket, and returns the
  exact `url` to connect to.

Connect to the returned `url` verbatim — never assemble the WebSocket URL
(host, path, account prefix) yourself; the topology is the server's to change.
Both lanes serve agent principals: an agent's client-credentials token can
poll the feed and mint stream tickets for its own live stream, and access
revocation drops an agent's socket exactly as it drops a user's. A ticket
minted on a delegated request carries its agent, so `self` on the socket it
opens resolves to the agent exactly as it does for that request's polls.

Mint a fresh ticket for every connection attempt: tickets expire in about two
minutes and are not refreshed by an open socket. A ticket is a replayable
bearer within that window — it is stateless and can open more than one
socket, so mint-per-connection is connector discipline, not server
enforcement. Every socket is bounded to a single subscription regardless.

###### Example JSON Response
<!-- START POST /events/stream_ticket.json -->
```json
{
  "ticket": "aBcD...",
  "expires_in": 120,
  "url": "wss://chat.3.basecamp.com/195539477?ticket=aBcD..."
}
```
<!-- END POST /events/stream_ticket.json -->

###### Copy as cURL

```shell
curl -s -X POST -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/events/stream_ticket.json
```

Live stream
-----------

Connect an Action Cable WebSocket client to the `url` from the mint, then
subscribe to `EventsChannel`:

```json
{"command":"subscribe","identifier":"{\"channel\":\"EventsChannel\",\"types\":\"message.created,chat.line.created\"}"}
```

No `Origin` header is required for non-browser clients; browser-embedded
clients always send their page origin, which must be a Basecamp origin.

Subscription parameters mirror the poll filters (`types`, `buckets`,
`creators`, `performers`, `exclude_performers` — `self` included — and
`actor_types`, with the same caps and bounds). Chat is high-volume and only streamed
when your `types` include chat types (or you subscribe unfiltered). Each
message is a wake-up payload:

```json
{
  "id": 1071915468,
  "kind": "message_created",
  "event_type": "message.created",
  "action": "created",
  "created_at": "2026-07-14T06:10:00.159Z",
  "bucket_id": 2085958499,
  "creator_id": 1049715945,
  "performed_by_id": null,
  "actor_type": "person",
  "recording_id": 1069479766,
  "visible_to_clients": false
}
```

Live frames carry two transport-only fields the poll payloads don't:
`actor_type` and `visible_to_clients`, which exist so the cable fleet can
filter without touching the database. Null-valued fields are present on the
wire, as in the example; `details` appears exactly when the type publishes
one.

### One subscription per connection

A ticket connection carries **exactly one** `EventsChannel` subscription.
Retransmitting the identical subscribe while awaiting confirmation is fine
(that's the stock client's behavior); a subscribe with different parameters is
rejected. To change filters, reconnect with a fresh ticket. Subscriptions to
any other channel are rejected, and malformed or oversized commands close the
connection with `"reconnect":false` and the disconnect reason
`invalid_event_stream_command` — a terminal protocol error, not a cue to retry.

### Liveness

The server pings ticket connections every 3 seconds (`{"type":"ping"}`).
Treat the connection as stale after two missed beats; a stock Action Cable
client's connection monitor detects that on its own jittered interval,
roughly 6–12 seconds.

The stream is usable only after the server confirms your subscription
(`confirm_subscription`) — an open socket is not a subscribed socket, since
confirmation waits on server-side stream registration. Start a confirmation
deadline (10 seconds is a good default) when you send the initial subscribe;
cancel it on confirmation, rejection, or disconnect. If the deadline lapses,
dispose the subscription and consumer, then reconnect with a fresh ticket.

An explicit subscription **rejection** (bad filters, restricted channel) does
not close the socket. Treat it as terminal configuration error: dispose the
consumer (closing the socket) and surface the error — do not reconnect into
the same rejection.

### Reconnection

**A stock Action Cable client cannot reconnect a ticket stream on its own.**
Its monitor reopens the connection with the same URL it first connected with,
so after any outage longer than the ~2-minute ticket lifetime it re-presents
an expired ticket and is rejected forever. Staleness *detection* works out of
the box; recovery does not.

Own reconnection in your wrapper:

1. Disable or intercept the stock automatic reconnect.
2. On disconnect (or a lapsed confirmation deadline), mint a fresh ticket
   asynchronously.
3. Create or reconnect the consumer with the new `url`, resubscribe, and wait
   for confirmation again.
4. Run at most one reconnect attempt at a time, with jittered backoff between
   attempts.

Client protocol
---------------

The recommended consumption loop:

1. Mint a ticket, connect to its `url`, subscribe, await confirmation, and
   **buffer** incoming live events.
2. Poll from your last durable position until `next` disappears from the
   envelope, persisting events and then the position as you go.
3. Drain the buffer, deduplicating by event id, then act on live events as
   they arrive.
4. Poll periodically (e.g. every 60 seconds) from your durable position to
   repair anything push missed.

**Live event ids never advance your durable position — only poll positions
do.** Positions persist across reconnects and restarts; tickets don't, so
mint a fresh ticket per connection.
