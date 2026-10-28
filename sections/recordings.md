Recordings
==========

Most of the data structures in the Basecamp 5 API are represented as "Recordings", with generic actions available to be performed.

A Ping's Campfire and its lines can be read here, but not changed: these actions answer `403 Forbidden` on them. See [Pings](pings.md#reading-and-writing-lines-in-a-ping).

Endpoints:

- [Get recordings](#get-recordings)
- [Get a recording](#get-a-recording)
- [Trash a recording](#trash-a-recording)
- [Archive a recording](#archive-a-recording)
- [Unarchive a recording](#unarchive-a-recording)
- [Move a recording to another project](#move-a-recording-to-another-project)
- [Copy a recording to another project](#copy-a-recording-to-another-project)
- [Get a filing](#get-a-filing)

Get recordings
--------------

* `GET /projects/recordings.json` will return a [paginated list][1] of records for the given `type` of recording.

**Required parameters**: `type`, which must be `Comment`, `Document`, `Door`, `Kanban::Card`, `Kanban::Step`, `Message`, `Question::Answer`, `Schedule::Entry`, `Todo`, `Todolist`, `Upload`, or `Vault`.

_Optional query parameters_:

* `bucket` - Single or comma separated list of [project][2] IDs. Default: All active projects visible to the current user.
* `status` - Options: `active`, `archived`, or `trashed`. Default: `active`
* `sort` - Options: `created_at` or `updated_at`. Default: `created_at`.
* `direction` - Options: `desc` or `asc`. Default: `desc`.

Examples: `/projects/recordings.json?type=Todo`, `/projects/recordings.json?type=Message&bucket=1`, `/projects/recordings.json?type=Document&bucket=1,2&sort=updated_at&direction=asc`


Get a recording
---------------

* `GET /recordings/2.json` will return the generic JSON representation of the recording with an ID of `2`.

This endpoint is useful when you have a recording ID but do not yet know its specific type. The response includes the recording's `type`, which can then be used to follow up with the corresponding type-specific endpoint if needed.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2.json
```


Trash a recording
-----------------

* `PUT /recordings/2/status/trashed.json` will mark the recording with an ID of `2` as trashed.

No parameters required. Returns `204 No Content` if successful.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/status/trashed.json
```


Archive a recording
-------------------

* `PUT /recordings/2/status/archived.json` will mark the recording with an ID of `2` as archived.

No parameters required. Returns `204 No Content` if successful.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/status/archived.json
```


Unarchive a recording
---------------------

* `PUT /recordings/2/status/active.json` will mark the recording with an ID of `2` as active.

No parameters required. Returns `204 No Content` if successful.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/status/active.json
```

Move a recording to another project
-----------------------------------

* `POST /recordings/2/moves.json` starts moving the recording with an ID of `2` into another project.

Moving runs in the background. The endpoint answers immediately with a [filing](#get-a-filing), which is then polled for its result. Once the move completes, the recording lives in the destination project under a new ID, which the completed filing reports.

**Required parameters**: one of

* `filing_destination_id` - the ID of the container the recording moves into. It must be the same kind of container the recording sits in now. Find tools in the destination project's `dock` array, from [Get a project](projects.md#get-a-project):
  * a message moves into a `message_board`.
  * a card moves into a `kanban_board` (card table). It lands in Triage, or in Done if it's completed. A card table column moves into a `kanban_board` too.
  * a document, upload, cloud file, Google document or folder moves into a `vault` (Docs & Files).
  * a schedule entry moves into a `schedule`.
  * a check-in question moves into a `questionnaire` (Automatic Check-ins).
  * an email forward moves into an `inbox` (Email Forwards).
  * a to-do list moves into a `todoset` (To-dos).
  * a to-do, or a to-do list group, moves into a to-do list, found with [Get to-do lists](todolists.md#get-to-do-lists). The list may be in the to-do's own project or another one, but it can't be a group, an archived or trashed list, or, for a move, the list the to-do is already in. A group moved into a list becomes a group in that list.
* `destination_project_id` - for a tool from a project's `dock` (a message board, card table, Docs & Files, schedule, and so on), the ID of the project it moves to. A tool has no container ID to name, so it's moved by project instead. This parameter applies to tools only. If a request for a tool gives both parameters, `destination_project_id` is used. A tool's `filing_destination_id` may instead be the ID of the destination project's dock.

_Optional parameters_:

* `parent_id` - when moving into a `vault`, the ID of a folder inside it to put the recording in.

Returns `201 Created` with the filing, and its URL in the `Location` header. Returns `403 Forbidden` if the recording can't be moved on its own (see below) or the current user isn't allowed to move it, `404 Not Found` if the destination isn't one the current user can move it into, `422 Unprocessable Entity` if the move can't start, such as when the recording is already being moved or the destination can't take it, and `400 Bad Request` if neither destination parameter is given.

Only the recordings listed above, and the dock tools, move on their own. Everything else moves only along with its parent and returns `403 Forbidden`: comments, attachments, card steps, check-in answers, hill chart updates, external links, card table columns that every card table has (Triage, Not now, Done and On hold), and anything outside a tool, such as client correspondence and approvals. To move one, move the recording or tool it belongs to.

A recording in the trash, or inside something that's in the trash, comes out of the trash in its destination as if it had been restored, and so does a copy of one, leaving the original in the trash.

A move through this endpoint always gives the recording a new ID, even within its project. To move a to-do into another list in its own project and keep its ID, [reposition it](todos.md#reposition-a-to-do) with a `parent_id` instead.

A move is safe to retry. While the first move is pending, a retry returns `422`, and once it's done, a retry returns `404` because the recording has moved.

###### Example JSON Request
<!-- START POST PAYLOAD /recordings/2/moves.json -->
```json
{
  "filing_destination_id": 1069480049
}
```
<!-- END POST PAYLOAD /recordings/2/moves.json -->

###### Example JSON Response
<!-- START POST /recordings/2/moves.json -->
```json
{
  "id": 4,
  "status": "pending",
  "type": "Move",
  "source_recording_id": 1069479351,
  "url": "https://3.basecampapi.com/195539477/filings/4.json"
}
```
<!-- END POST /recordings/2/moves.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"filing_destination_id":1069480049}' -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/moves.json
```

To move a tool, name the project instead:

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"destination_project_id":2085958505}' -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/moves.json
```


Copy a recording to another project
-----------------------------------

* `POST /recordings/2/copies.json` starts copying the recording with an ID of `2` into another project.

Copying works like [moving](#move-a-recording-to-another-project), and takes the same `filing_destination_id`, `destination_project_id` and `parent_id` parameters, except the original stays where it is. The same recordings copy on their own, except the Email Forwards tool, which can't be copied. A copied card lands in Triage, or in Done if it's completed, as a moved one does.

_Optional parameters_:

* `include_comments` - copy the recording's comments too. Defaults to `false`.

Returns `201 Created` with the filing, and its URL in the `Location` header. Returns `403 Forbidden` if the recording can't be copied on its own, `404 Not Found` if the destination isn't one the current user can copy it into, `422 Unprocessable Entity` if the copy can't start, such as when the recording is being moved or the destination can't take it, and `400 Bad Request` if neither destination parameter is given.

A copy is not safe to retry blindly, since each request makes another copy. Check the first filing's status before trying again.

###### Example JSON Request
<!-- START POST PAYLOAD /recordings/2/copies.json -->
```json
{
  "filing_destination_id": 1069480049,
  "include_comments": true
}
```
<!-- END POST PAYLOAD /recordings/2/copies.json -->

###### Example JSON Response
<!-- START POST /recordings/2/copies.json -->
```json
{
  "id": 5,
  "status": "pending",
  "type": "Copy",
  "source_recording_id": 1069479351,
  "url": "https://3.basecampapi.com/195539477/filings/5.json"
}
```
<!-- END POST /recordings/2/copies.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"filing_destination_id":1069480049,"include_comments":true}' -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/copies.json
```


Get a filing
------------

* `GET /filings/4.json` returns the current state of the move or copy with an ID of `4`.

`type` is `Move` or `Copy`. `status` is `pending` or `processing` while the work is in progress, `completed` when it's done, and `failed` if it couldn't be done. Poll until it leaves `pending` and `processing`.

A completed filing carries the recording it made under `destination_recording`. Follow its `url` for the full recording. If that recording has since been permanently deleted, the filing returns `404 Not Found`.

Only the person who started the move or copy can read it. Anyone else gets `404 Not Found`.

###### Example JSON Response
<!-- START GET /filings/4.json -->
```json
{
  "id": 4,
  "status": "completed",
  "type": "Move",
  "source_recording_id": 1069479351,
  "url": "https://3.basecampapi.com/195539477/filings/4.json",
  "destination_recording": {
    "id": 1069480270,
    "type": "Message",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/messages/1069480270.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069480270"
  }
}
```
<!-- END GET /filings/4.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  https://3.basecampapi.com/$ACCOUNT_ID/filings/4.json
```


Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/recordings/2.json` → [Get a recording](#get-a-recording)
* `PUT /buckets/1/recordings/2/status/trashed.json` → [Trash a recording](#trash-a-recording)
* `PUT /buckets/1/recordings/2/status/archived.json` → [Archive a recording](#archive-a-recording)
* `PUT /buckets/1/recordings/2/status/active.json` → [Unarchive a recording](#unarchive-a-recording)
* `POST /buckets/1/recordings/2/moves.json` → [Move a recording to another project](#move-a-recording-to-another-project)
* `POST /buckets/1/recordings/2/copies.json` → [Copy a recording to another project](#copy-a-recording-to-another-project)

[1]: ../README.md#pagination
[2]: projects.md#projects
