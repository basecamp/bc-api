The Basecamp API
=================

Connecting to Basecamp? Here's how:

- **AI agents** — Install the [Basecamp Skills](https://github.com/basecamp/skills) or the [Basecamp CLI](https://github.com/basecamp/basecamp-cli).
- **Integrating with your app or service** — The [Basecamp SDK](https://github.com/basecamp/basecamp-sdk) provides full-featured API clients and an [OpenAPI spec](https://github.com/basecamp/basecamp-sdk/blob/main/openapi.json) for code generation.
- **Going fully custom** — The OpenAPI spec and this REST API reference cover authentication, pagination, and every endpoint in detail.


Making a request
----------------

All URLs start with **`https://3.basecampapi.com/999999999/`**. URLs are HTTPS only. The path is prefixed with the account ID, but no `/api/v1` API prefix. Also, note the different domain!

To make a request for all the projects on your account, append the `projects` index path to the base URL to form something like `https://3.basecampapi.com/999999999/projects.json`. In cURL, it looks like this:

```shell
curl -H "Authorization: Bearer $ACCESS_TOKEN" -A 'MyApp (yourname@example.com)' https://3.basecampapi.com/999999999/projects.json
```

To create something, it's the same idea, but you also have to include the `Content-Type` header and the JSON data:

```shell
curl -H "Authorization: Bearer $ACCESS_TOKEN" \
  -H 'Content-Type: application/json' \
  -A 'User-Agent: MyApp (yourname@example.com)' \
  -d '{ "name": "My new project!" }' \
  https://3.basecampapi.com/999999999/projects.json
```

Throughout the Basecamp API docs, we include "Copy as cURL" examples. To try the examples in your shell, copy your OAuth 2.0 access token into your clipboard and run:

```shell
export ACCESS_TOKEN=PASTE_ACCESS_TOKEN_HERE
export ACCOUNT_ID=999999999
```

Then you should be able to copy/paste any example from the docs. After pasting a cURL example, you can pipe it to a JSON pretty printer to make it more readable. Try [jsonpp](https://jmhodges.github.io/jsonpp/) or `json_pp` on OSX:

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/999999999/projects.json | json_pp
```


Flat routes
-----------

Every resource in the Basecamp API is uniquely identified by its own ID. You can access any resource directly without including its project (bucket) in the URL:

```
GET /todos/67890.json
GET /messages/12345.json
GET /todolists/456/todos.json
```

These **flat routes** are the canonical form for all new integrations. The project context is derived server-side from the resource itself, so you rarely need to supply a `bucket_id`. A few project-level collection endpoints (message types, webhooks index/create, tools) still require the project-scoped form — these are noted in their respective sections.

For listing and creating resources under a parent, use the parent's ID directly:

```
GET  /todolists/456/todos.json        # list to-dos in a to-do list
POST /todolists/456/todos.json        # create a to-do in a to-do list
GET  /message_boards/789/messages.json # list messages on a board
POST /recordings/123/comments.json     # comment on any recording
```

The previous project-scoped form — `/buckets/{project_id}/...` — remains available and will continue to work in perpetuity, but is considered legacy. All endpoint documentation in this guide uses flat routes as the primary form, with legacy equivalents noted at the bottom of each section.


Authentication
--------------

As mentioned above, to authenticate you must use OAuth 2.0. OAuth 2.0 allows users to authorize your application to use Basecamp on their behalf without having to copy/paste API tokens or touch sensitive login information.

Read the [authentication guide](sections/authentication.md) to get started.


Identifying your application
----------------------------

You must include a `User-Agent` header with **both**:

* The name of your application
* A link to your application or your email address

We use this information to get in touch if you're doing something wrong (so we can warn you before you're blacklisted) or something awesome (so we can congratulate you). Here are examples of acceptable `User-Agent` headers:

* `User-Agent: Freshbooks (http://freshbooks.com/contact.php)`
* `User-Agent: Fabian's Ingenious Integration (fabian@example.com)`

If you don't include a `User-Agent` header, you'll get a `400 Bad Request` response.


JSON only
---------

We use JSON for all API data. The style is no root element and snake\_case for object keys. This means that you have to send the `Content-Type` header `Content-Type: application/json; charset=utf-8` when you're POSTing or PUTing data into Basecamp. All API URLs end in `.json` to indicate that they return JSON. Alternatively you can send `Accept: application/json`.

You'll receive a `415 Unsupported Media Type` response code if you don't include the `Content-Type` header.


Pagination
----------

Most collection APIs paginate their results. The number of requests that'll appear on each page is variable. In most cases, we use a [geared pagination ratio](https://github.com/basecamp/geared_pagination) with 15 results on page 1, 30 on page 2, 50 on 3, and then 100 on 4 and above. The Basecamp API follows the [RFC5988 convention](https://tools.ietf.org/html/rfc5988) of using the `Link` header to provide URLs for the `next` page. Follow this convention to retrieve the next page of data—please don't build the pagination URLs yourself!

Here's an example response header from requesting the third page of [messages](sections/messages.md#messages):

```
Link: <https://3.basecampapi.com/999999999/message_boards/3/messages.json?page=4>; rel="next"
```

If the `Link` header is blank, that's the last page. The Basecamp API also provides the `X-Total-Count` header, which displays the total number of resources in the collection you are fetching.


Using HTTP caching
------------------

You must use HTTP freshness headers to speed up your application and lighten the load on our servers. Most API responses will include an `ETag` or `Last-Modified` header. When you first request a resource, store these values. On subsequent requests, submit them back to us as `If-None-Match` and `If-Modified-Since`, respectively. If the resource hasn't changed since your last request, you'll get a `304 Not Modified` response with no body, saving you the time and bandwidth of sending something you already have.


Handling errors
---------------

API clients must expect and gracefully handle transient server errors and rate limits. We recommend baking graceful 5xx and 429 retries into your integration from the beginning so errors are handled automatically.

### Rate limiting (429 Too Many Requests)

We return a [429 Too Many Requests](http://tools.ietf.org/html/draft-nottingham-http-new-status-02#section-4) response when you've exceeded a rate limit. Consult the `Retry-After` response header to determine how long to wait (in seconds) before retrying the request.

Plan ahead to gracefully handle the failure modes that API backpressure will exert on your integration. Multiple rate limits are in effect, e.g. for GET vs POST requests and per-second/hour/day limits, and they're adjusted dynamically, so responding to them dynamically is essential, particularly at high traffic levels.

For a sense of scale, the first rate limit you'll commonly encounter is currently 50 requests per 10 second period per IP address.

### [5xx server errors](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#5xx_Server_errors)

If Basecamp is having trouble, you will get a response with a 5xx status code indicating a server error. 500 (Internal Server Error), 502 (Bad Gateway), 503 (Service Unavailable), and 504 (Gateway Timeout) may be retried with [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff).

### 404 Not Found

API requests may 404 due to deleted content, an inactive account, missing user permissions, etc. Detect these conditions to give your users a clear explanation about why they can't connect to Basecamp. Do not automatically retry these requests.

* Inactive account. 404 Not Found response with a `Reason: Account Inactive` header. Due to an expired trial or account suspension. All API requests to an inactive account will fail, so we recommend detecting and disabling the account in your integration as well.
* Inaccessible items. 404 Not Found response. Due to a deleted item or insufficient permissions.


Rich text content
-----------------

Many resources, including messages, documents, and comments, represent their content as rich text in HTML. Rich text content may contain lists, block quotes, simple formatting, and inline attachments such as mentions, images, and files.

See the [Rich text](sections/rich_text.md) section for more information about working with HTML and attachments in rich text content.


Key concepts
------------

Understanding Basecamp's domain model helps you navigate the API effectively.

### The bucket/project relationship

Every project has exactly one **bucket**—its storage container for all content. The `bucket_id` and project ID are the same value.

With flat routes, you don't need to know the bucket ID to access a resource — just use the resource's own ID:

```
GET /todos/67890.json          # access a to-do directly
GET /todolists/456/todos.json  # list to-dos in a to-do list
```

The legacy project-scoped form includes the bucket explicitly:

```
GET /buckets/12345/todos/67890.json
             ↑
        This is the project ID
```

Both forms return identical responses. Flat routes are preferred for all new integrations.

### Recordings: bucket contents

A **recording** is an entry in a bucket. Every piece of content—to-dos, messages, documents, comments, uploads, schedule entries, and 50+ other types—has a recording that tracks:

- **Status**: `active`, `archived`, `trashed` (publication state, separate from completion)
- **Tree structure**: parent/child relationships for nesting
- **Visibility**: whether clients can see the content
- **Subscriptions**: who gets notified of changes

The [recordings endpoint](sections/recordings.md) queries across projects by type (required): `?type=Todo`, `?type=Message`, etc.

### The dock: project tools

Each project has a **dock**—a list of available tools. Check the dock to discover what's enabled:

```json
"dock": [
  { "name": "message_board", "enabled": true, "url": "...", "id": 123 },
  { "name": "todoset", "enabled": true, "url": "...", "id": 456 },
  { "name": "schedule", "enabled": false, "url": "...", "id": 789 }
]
```

The dock is your source of truth for available tools. Common ones: `message_board`, `todoset`, `vault` (files), `schedule`, `chat` (campfire), `questionnaire` (automatic check-ins), `inbox` (email forwards), `kanban_board` (card table).

**Always check `enabled: true`** before using a tool—not all projects have all tools turned on.

### To-do hierarchy

To-dos have a specific container structure:

```
Project
  └── To-do set (exactly one per project, find via dock)
        ├── To-do list "Launch tasks"
        │     ├── To-do item
        │     └── To-do item
        └── To-do list "Research"
              └── To-do item
```

To create a to-do list, POST to the **to-do set**:
`POST /todosets/{todoset_id}/todolists.json`

### Similar patterns for other tools

The to-do set pattern repeats for other tools. Each is a singleton container accessed via the dock:

| Tool | Container | Contains |
|------|-----------|----------|
| Message board | One per project | Messages |
| Vault | One per project | Documents, uploads, folders |
| Schedule | One per project | Schedule entries |
| Questionnaire | One per project | Questions (check-ins) |
| Card table | One per project | Columns → Cards |

### Parent relationships

Content items have a `parent` object showing their container:

```json
{
  "id": 67890,
  "type": "Todo",
  "parent": {
    "id": 11111,
    "type": "Todolist",
    "title": "Launch tasks",
    "url": "..."
  }
}
```

Use `parent` for navigation. A to-do's parent is its to-do list. A message's parent is the message board.

### People, not users

The resource is called **person** (not user). Endpoints:
- `/people.json` — list people in account
- `/people/{id}.json` — single person
- `/projects/{id}/people.json` — people in a project
- `/my/profile.json` — current authenticated user (GET and PUT)

### To-do specifics

**Completion**: To-dos have a boolean `completed` field. By default, endpoints return active, pending (not completed) items. Use `?completed=true` for completed items. Use `?status=archived` or `?status=trashed` to see those.

**Assignees**: Always an array, even for single assignment. When creating: `"assignee_ids": [123]`.

### Status vs completion

Don't confuse **recording status** with **to-do completion**:

- **Status** (`active`, `archived`, `trashed`): Publication state. Applies to all recordings.
- **Completed** (`true`/`false`): Whether a to-do is done. Only applies to to-dos, cards, and card steps.

A to-do can be `completed: true` and `status: "active"` (done but not archived).


API endpoints
-------------
- [Authentication](sections/authentication.md#authentication)
<!-- START API ENDPOINTS -->
- [Account](sections/account.md#account)
- [Attachments](sections/attachments.md#attachments)
- [Boosts](sections/boosts.md#boosts)
- [Calendars](sections/calendars.md#calendars)
- [Campfires](sections/campfires.md#campfires)
- [Card table cards](sections/card_table_cards.md#card-table-cards)
- [Card table columns](sections/card_table_columns.md#card-table-columns)
- [Card table steps](sections/card_table_steps.md#card-table-steps)
- [Card table wormholes](sections/card_table_wormholes.md#card-table-wormholes)
- [Card tables](sections/card_tables.md#card-tables)
- [Chatbots](sections/chatbots.md#chatbots)
- [Client approvals](sections/client_approvals.md#client-approvals)
- [Client correspondences](sections/client_correspondences.md#client-correspondences)
- [Client replies](sections/client_replies.md#client-replies)
- [Client visibility](sections/client_visibility.md#client-visibility)
- [Cloud files](sections/cloud_files.md#cloud-files)
- [Comments](sections/comments.md#comments)
- [Documents](sections/documents.md#documents)
- [Drafts](sections/drafts.md#drafts)
- [Events](sections/events.md#events)
- [Everything](sections/everything.md#everything)
- [External links](sections/external_links.md#external-links)
- [Forwards](sections/forwards.md#forwards)
- [Gauges](sections/gauges.md#gauges)
- [Google documents](sections/google_documents.md#google-documents)
- [Hill charts](sections/hill_charts.md#hill-charts)
- [Inbox replies](sections/inbox_replies.md#inbox-replies)
- [Inboxes](sections/inboxes.md#inboxes)
- [Lineup Markers](sections/lineup_markers.md#lineup-markers)
- [Message Boards](sections/message_boards.md#message-boards)
- [Message Types](sections/message_types.md#message-types)
- [Messages](sections/messages.md#messages)
- [My assignments](sections/my_assignments.md#my-assignments)
- [My notes](sections/my_notes.md#my-notes)
- [My notifications](sections/my_notifications.md#my-notifications)
- [Out of office](sections/out_of_office.md#out-of-office)
- [People](sections/people.md#people)
- [Projects](sections/projects.md#projects)
- [Question answers](sections/question_answers.md#question-answers)
- [Question reminders](sections/question_reminders.md#question-reminders)
- [Questionnaires](sections/questionnaires.md#questionnaires)
- [Questions](sections/questions.md#questions)
- [Recordings](sections/recordings.md#recordings)
- [Reports](sections/reports.md#reports)
- [Schedule entries](sections/schedule_entries.md#schedule-entries)
- [Schedules](sections/schedules.md#schedules)
- [Search](sections/search.md#search)
- [Subscriptions](sections/subscriptions.md#subscriptions)
- [Templates](sections/templates.md#templates)
- [Timeline](sections/timeline.md#timeline)
- [Timesheets](sections/timesheets.md#timesheets)
- [To-do list groups](sections/todolist_groups.md#to-do-list-groups)
- [To-do lists](sections/todolists.md#to-do-lists)
- [To-do sets](sections/todosets.md#to-do-sets)
- [To-dos](sections/todos.md#to-dos)
- [Tools](sections/tools.md#tools)
- [Uploads](sections/uploads.md#uploads)
- [Vaults](sections/vaults.md#vaults)
- [Webhooks](sections/webhooks.md#webhooks)

<!-- END API ENDPOINTS -->

Basecamp 2 and Basecamp Classic APIs
-------------------------------------

The Basecamp API is not compatible with the [Basecamp Classic API](https://github.com/basecamp/basecamp-classic-api) or the [Basecamp 2 API](https://github.com/basecamp/bcx-api). All integrations will start fresh with the new API. The core ingredients are the same, though: Basecamp is a REST-style API that uses JSON for serialization and OAuth 2.0 for authentication.


What's different from earlier APIs?
------------------------------------

If you've used a previous version of the Basecamp API, you need to adapt your integration code. Here are some notable changes:

- We require OAuth 2.0 for [authentication](#authentication)—no more Basic authentication
- [Pagination](#pagination) is performed via the `Link` and `X-Total-Count` headers


Listing your application
------------------------

To add your application to our public list of Basecamp integrations, go to [https://github.com/basecamp/bc3-integrations](https://github.com/basecamp/bc3-integrations) and open a pull request.

Getting Help
------------

If you have a question about the API, please [open a support ticket](https://basecamp.com/support).


Conduct
-------

Please note that this project is released with a [Contributor Code of Conduct](CONDUCT.md). By participating in discussions about the Basecamp API, you agree to abide by these terms.


License
-------

These API docs are licensed under [Creative Commons (CC BY-SA 4.0)](http://creativecommons.org/licenses/by-sa/4.0/). Please share, remix, and distribute as you see fit.
