My notes
========

Available since Basecamp 5: a per-person notebook — a single rich-text note
that follows the user across devices. Each authenticated user has at most one
note; the API treats it as a singleton resource at `/my/notes.json`. Updates are
versioned: each save records a new revision behind the scenes while the API
always returns the current note.

Endpoints:

- [Get the note](#get-the-note)
- [Update the note](#update-the-note)

Get the note
------------

* `GET /my/notes.json` returns the authenticated user's note. If the user
  has not yet written anything, the response shape is the same, `content` is
  empty, and `id`, `created_at`, and `updated_at` are `null` — the note record
  is created on first update.

###### Example JSON Response
<!-- START GET /my/notes.json -->
```json
{
  "id": 5,
  "type": "Notebook::Note",
  "created_at": "2026-07-21T00:02:30.308Z",
  "updated_at": "2026-07-21T00:02:30.308Z",
  "content": "<div dir=\"auto\">Things to remember…</div>",
  "content_attachments": [],
  "url": "https://3.basecampapi.com/195539477/my/notes.json",
  "app_url": "https://3.basecamp.com/195539477/my/navigation/notes"
}
```
<!-- END GET /my/notes.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/notes.json
```

Update the note
---------------

* `PUT /my/notes.json` replaces the note's content, recording a new revision.
  The first update also creates the underlying notebook if the user did not
  have one yet.

###### Permitted parameters

| Param      | Type | Description |
| ---------- | ---- | ----------- |
| `content`  | HTML | The note's rich-text body. |

###### Example JSON Request
<!-- START PUT PAYLOAD /my/notes.json -->
```json
{
  "note": {
    "content": "<div>Things to remember…</div>"
  }
}
```
<!-- END PUT PAYLOAD /my/notes.json -->

Returns `200 OK` with the updated note's JSON shape.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"note":{"content":"<div>Things to remember…</div>"}}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/my/notes.json
```
