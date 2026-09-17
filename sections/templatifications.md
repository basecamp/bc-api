Templatifications
=================

Endpoints:

- [Templatify a to-do list or card table](#templatify-a-to-do-list-or-card-table)
- [Get a templatification](#get-a-templatification)

Templatifying turns a to-do list or card table that already exists in a project into a template, where it joins the [to-do list templates](template_library.md) or [card table templates](card_table_templates.md). Nothing else can be templatified.

It runs in the background. The endpoint answers immediately with a templatification, which is then polled for its result.

Templatify a to-do list or card table
-------------------------------------

* `POST /buckets/1/recordings/2/templatifications.json` starts templatifying recording `2` into the template library.

Every attribute is optional, and a request with no body at all is valid. An unnamed template takes the title of the recording it was made from.

* `template_name` - what to call the template. Defaults to the source's own title.
* `copy_comments` - carry the comments across. Defaults to `false`.
* `copy_assignments` - carry assignees and the people involved across, adding them to the library if they aren't already there. Defaults to `false`.
* `move_cards_to_triage` - gather the cards into the Triage column instead of leaving them where they sit. **Card tables only**, and ignored for a to-do list. Defaults to `false`.

Answers `201 Created` with the record described below. `403 Forbidden` if the recording isn't a to-do list or card table, if the caller is a client, or if the caller can't edit the project the work lives in.

###### Example JSON Request
<!-- START POST PAYLOAD /buckets/1/recordings/2/templatifications.json -->
```json
{
  "template_name": "Client onboarding",
  "copy_assignments": true
}
```
<!-- END POST PAYLOAD /buckets/1/recordings/2/templatifications.json -->

###### Example JSON Response
<!-- START POST /buckets/1/recordings/2/templatifications.json -->
```json
{
  "id": 3,
  "status": "pending",
  "source_recording_id": 1069479864,
  "url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479864/templatifications/3.json"
}
```
<!-- END POST /buckets/1/recordings/2/templatifications.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"template_name":"Client onboarding","copy_assignments":true}' -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/recordings/2/templatifications.json
```

Get a templatification
----------------------

* `GET /buckets/1/recordings/2/templatifications/3.json` returns the current state of the templatification.

`status` is `pending` or `processing` while the work is in progress, `completed` when the template is ready, and `failed` if it could not be made. Poll until it leaves `pending` and `processing`.

A completed templatification carries the template it made, under `destination_todolist` or `destination_card_table` depending on the kind of recording it came from. These are the same keys, holding the same shapes, that [a template copy](template_library.md#get-a-template-copy) reports.

Only the person who started the templatification can read it. Anyone else gets `404 Not Found`.

###### Example JSON Response
<!-- START GET /buckets/1/recordings/2/templatifications/3.json -->
```json
{
  "id": 3,
  "status": "completed",
  "source_recording_id": 1069479864,
  "url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479864/templatifications/3.json",
  "destination_todolist": {
    "id": 1069480319,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-09-12T08:22:06.428Z",
    "updated_at": "2026-09-12T08:22:06.708Z",
    "title": "Client onboarding",
    "inherits_status": true,
    "type": "Todolist",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480319.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/todolists/1069480319",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDMxOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--ccc56c890ea4527b3c54a99f993c74f032b3e2be.json",
    "comments_count": 0,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480319/comments.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480319/boosts.json",
    "bubble_up_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480319/bubble_up.json",
    "position": 1,
    "parent": {
      "id": 1069478890,
      "title": "To-do List Templates",
      "type": "Todoset",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958495/todosets/1069478890.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/todosets/1069478890"
    },
    "bucket": {
      "id": 2085958495,
      "name": "To-do List Templates",
      "type": "TemplateLibrary"
    },
    "creator": {
      "id": 1049715913,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
      "name": "Victor Cooper",
      "personable_type": "User",
      "title": "Chief Strategist",
      "tagline": "Don't let your dreams be dreams",
      "location": "Chicago, IL",
      "created_at": "2026-09-12T08:17:09.797Z",
      "updated_at": "2026-09-12T08:17:10.372Z",
      "email_address": "victor@honchodesign.com",
      "bio": "Don't let your dreams be dreams",
      "admin": true,
      "owner": true,
      "client": false,
      "employee": true,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
      "company": {
        "id": 1033447817,
        "name": "Honcho Design"
      },
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    },
    "description": "",
    "description_attachments": [],
    "completed": false,
    "completed_ratio": "0/5",
    "name": "Client onboarding",
    "color": null,
    "groups_url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480319/groups.json",
    "todos_url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480319/todos.json",
    "app_todos_url": "https://3.basecamp.com/195539477/buckets/2085958495/todolists/1069480319/todos",
    "comments_app_url": "https://3.basecamp.com/195539477/buckets/2085958495/recordings/1069480319/comments"
  }
}
```
<!-- END GET /buckets/1/recordings/2/templatifications/3.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/recordings/2/templatifications/3.json
```
