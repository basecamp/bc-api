To-do list templates
====================

Endpoints:

- [Get the template library](#get-the-template-library)
- [Create a to-do list template](#create-a-to-do-list-template)
- [Create a to-do list from a template](#create-a-to-do-list-from-a-template)
- [Get a template copy](#get-a-template-copy)

Get the template library
------------------------

* `GET /template_library/todolists.json` returns the account's to-do list template library, its to-do set, and its active to-do list templates in title order.

The bucket and to-do set IDs can be used with the existing [to-do list](todolists.md) and [to-do](todos.md) endpoints to create and manage template contents. [Card table templates](card_table_templates.md) have their own endpoints.

`GET /template_library.json` is the former address of this endpoint, from when the library held only to-do list templates. It still answers, redirecting here and preserving the requested format. Prefer the address above: the redirect costs a round trip and says nothing about which kind of template it returns.

###### Example JSON Response
<!-- START GET /template_library/todolists.json -->
```json
{
  "bucket": {
    "id": 2085958495,
    "name": "To-do List Templates",
    "type": "TemplateLibrary"
  },
  "todoset": {
    "id": 1069478890,
    "title": "To-do List Templates",
    "type": "Todoset",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958495/todosets/1069478890.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/todosets/1069478890"
  },
  "todolists": [
    {
      "id": 1069480315,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-09-12T08:21:58.922Z",
      "updated_at": "2026-09-12T08:21:59.692Z",
      "title": "Assigned launch checklist",
      "inherits_status": true,
      "type": "Todolist",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480315.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/todolists/1069480315",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDMxNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--17548aea6556917fc5cb0b2da02e6edf99683c48.json",
      "comments_count": 0,
      "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480315/comments.json",
      "boosts_count": 0,
      "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480315/boosts.json",
      "bubble_up_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480315/bubble_up.json",
      "position": 2,
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
      "completed_ratio": "0/1",
      "name": "Assigned launch checklist",
      "color": null,
      "groups_url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480315/groups.json",
      "todos_url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480315/todos.json",
      "app_todos_url": "https://3.basecamp.com/195539477/buckets/2085958495/todolists/1069480315/todos",
      "comments_app_url": "https://3.basecamp.com/195539477/buckets/2085958495/recordings/1069480315/comments"
    },
    {
      "id": 1069480317,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-09-12T08:22:00.082Z",
      "updated_at": "2026-09-12T08:22:00.082Z",
      "title": "New hire setup",
      "inherits_status": true,
      "type": "Todolist",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480317.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/todolists/1069480317",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDMxNz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--b3397ba9708eefe03ea717fa47674178dc50e830.json",
      "comments_count": 0,
      "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480317/comments.json",
      "boosts_count": 0,
      "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480317/boosts.json",
      "bubble_up_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480317/bubble_up.json",
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
      "completed_ratio": "0/0",
      "name": "New hire setup",
      "color": null,
      "groups_url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480317/groups.json",
      "todos_url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480317/todos.json",
      "app_todos_url": "https://3.basecamp.com/195539477/buckets/2085958495/todolists/1069480317/todos",
      "comments_app_url": "https://3.basecamp.com/195539477/buckets/2085958495/recordings/1069480317/comments"
    },
    {
      "id": 1069480314,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-09-12T08:21:58.556Z",
      "updated_at": "2026-09-12T08:21:58.556Z",
      "title": "Project kickoff",
      "inherits_status": true,
      "type": "Todolist",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480314.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/todolists/1069480314",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDMxND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--2e1c2130d64df5d6cf4baa60fabe92a89f6958a4.json",
      "comments_count": 0,
      "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480314/comments.json",
      "boosts_count": 0,
      "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480314/boosts.json",
      "bubble_up_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480314/bubble_up.json",
      "position": 3,
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
      "completed_ratio": "0/0",
      "name": "Project kickoff",
      "color": null,
      "groups_url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480314/groups.json",
      "todos_url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480314/todos.json",
      "app_todos_url": "https://3.basecamp.com/195539477/buckets/2085958495/todolists/1069480314/todos",
      "comments_app_url": "https://3.basecamp.com/195539477/buckets/2085958495/recordings/1069480314/comments"
    }
  ]
}
```
<!-- END GET /template_library/todolists.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  https://3.basecampapi.com/$ACCOUNT_ID/template_library/todolists.json
```

Create a to-do list template
----------------------------

* `POST /template_library/todolists.json` creates an empty to-do list template.

* `name` - what to call the template. Required.
* `description` - rich text describing the template. Optional.

Answers `201 Created` with the template. Fill it in with the [to-do](todos.md) endpoints, using the returned ID. To start from a to-do list that already exists in a project, [templatify it](templatifications.md) instead.

###### Example JSON Request
<!-- START POST PAYLOAD /template_library/todolists.json -->
```json
{
  "name": "New hire setup"
}
```
<!-- END POST PAYLOAD /template_library/todolists.json -->

###### Example JSON Response
<!-- START POST /template_library/todolists.json -->
```json
{
  "id": 1069480317,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-09-12T08:22:00.082Z",
  "updated_at": "2026-09-12T08:22:00.082Z",
  "title": "New hire setup",
  "inherits_status": true,
  "type": "Todolist",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480317.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/todolists/1069480317",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDMxNz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--b3397ba9708eefe03ea717fa47674178dc50e830.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480317/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480317/boosts.json",
  "bubble_up_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480317/bubble_up.json",
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
    "updated_at": "2026-09-12T03:17:10.372-05:00",
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
  "completed_ratio": "0/0",
  "name": "New hire setup",
  "color": null,
  "groups_url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480317/groups.json",
  "todos_url": "https://3.basecampapi.com/195539477/buckets/2085958495/todolists/1069480317/todos.json",
  "app_todos_url": "https://3.basecamp.com/195539477/buckets/2085958495/todolists/1069480317/todos",
  "comments_app_url": "https://3.basecamp.com/195539477/buckets/2085958495/recordings/1069480317/comments"
}
```
<!-- END POST /template_library/todolists.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"name":"New hire setup"}' -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/template_library/todolists.json
```

Create a to-do list from a template
------------------------------------

* `POST /template_library/copies.json` starts copying a to-do list template into a project's to-do set.

**Required parameters**:

* `template_recording_id` - the ID of a to-do list in the template library.
* `destination_project_id` - the ID of the [project](projects.md) to copy into. The to-do list lands in its to-do set.

A `destination_parent_id` naming the to-do set is accepted instead, for callers that already have one.

###### Example JSON Request

<!-- START POST PAYLOAD /template_library/copies.json -->
```json
{
  "template_recording_id": 1069480314,
  "destination_project_id": 2085958504
}
```
<!-- END POST PAYLOAD /template_library/copies.json -->

A successful request returns `201 Created` with a copy resource. Follow its `url` to track progress.

###### Example JSON Response
<!-- START POST /template_library/copies.json -->
```json
{
  "id": 2,
  "status": "pending",
  "source_recording_id": 1069480314,
  "destination_parent_id": 1069479830,
  "url": "https://3.basecampapi.com/195539477/template_library/copies/2.json"
}
```
<!-- END POST /template_library/copies.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"template_recording_id":1069480314,"destination_project_id":2085958504}' -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/template_library/copies.json
```

When the template contains assignments or completion subscriptions for people who do not have access to the destination project, the response is `422 Unprocessable Entity` and identifies the people who would be added:

<!-- START POST /template_library/copies.json (confirmation required) -->
```json
{
  "error": "people_confirmation_required",
  "people": [
    {
      "id": 1049715915,
      "name": "Amy Rivera",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMtkkT4=--9927c47a4cbee30a7f9aea667882496aba799149/avatar"
    }
  ]
}
```
<!-- END POST /template_library/copies.json (confirmation required) -->

Repeat the request with `adding_people_confirmed` set to `true` to grant those people access and start the copy.

Get a template copy
-------------------

* `GET /template_library/copies/2.json` returns the current state of a template copy.

Only the person who started the copy can retrieve it. Requests from anyone else return `404 Not Found`, so poll with the same credentials that created the copy.

The status is `pending`, `processing`, `completed`, or `failed`. Poll the URL no more than once per second while the copy is pending or processing. A completed response includes the newly created to-do list.

###### Example JSON Response
<!-- START GET /template_library/copies/2.json -->
```json
{
  "id": 2,
  "status": "completed",
  "source_recording_id": 1069480314,
  "destination_parent_id": 1069479830,
  "url": "https://3.basecampapi.com/195539477/template_library/copies/2.json",
  "destination_todolist": {
    "id": 1069480318,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-09-12T08:22:02.924Z",
    "updated_at": "2026-09-12T08:22:02.994Z",
    "title": "Project kickoff",
    "inherits_status": true,
    "type": "Todolist",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todolists/1069480318.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todolists/1069480318",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDMxOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--bd1dfbe4497ccccd37f42e32f2ac77a9059a6229.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480318/subscription.json",
    "comments_count": 0,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480318/comments.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480318/boosts.json",
    "bubble_up_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480318/bubble_up.json",
    "position": 3,
    "parent": {
      "id": 1069479830,
      "title": "To-dos",
      "type": "Todoset",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todosets/1069479830.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todosets/1069479830"
    },
    "bucket": {
      "id": 2085958504,
      "name": "The Leto Laptop",
      "type": "Project"
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
    "completed_ratio": "0/0",
    "name": "Project kickoff",
    "color": null,
    "groups_url": "https://3.basecampapi.com/195539477/buckets/2085958504/todolists/1069480318/groups.json",
    "todos_url": "https://3.basecampapi.com/195539477/buckets/2085958504/todolists/1069480318/todos.json",
    "app_todos_url": "https://3.basecamp.com/195539477/buckets/2085958504/todolists/1069480318/todos",
    "comments_app_url": "https://3.basecamp.com/195539477/buckets/2085958504/recordings/1069480318/comments"
  }
}
```
<!-- END GET /template_library/copies/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  https://3.basecampapi.com/$ACCOUNT_ID/template_library/copies/2.json
```
