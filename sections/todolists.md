To-do lists
===========

Endpoints:

- [Get to-do lists](#get-to-do-lists)
- [Get a to-do list](#get-a-to-do-list)
- [Create a to-do list](#create-a-to-do-list)
- [Update a to-do list](#update-a-to-do-list)
- [Trash a to-do list][trash]

Get to-do lists
---------------

* `GET /todosets/3/todolists.json` will return a [paginated list][pagination] of active to-do lists in the to-do set with ID of `3`.

To get the to-do set ID for a project, see the [Get to-do set][todoset] endpoint.

_Optional query parameters_:

* `status` - when set to `archived` or `trashed`, will return archived or trashed to-do lists that are in this to-do set.

###### Example JSON Response
<!-- START GET /todosets/3/todolists.json -->
```json
[
  {
    "id": 1069480012,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-05-12T04:27:00.000Z",
    "updated_at": "2026-07-21T00:06:16.451Z",
    "title": "Strategy ideas",
    "inherits_status": true,
    "type": "Todolist",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069480012.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069480012",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDAxMj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--cfb66070fa4900acb4d47211d84e218c14831c7a.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480012/subscription.json",
    "comments_count": 0,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480012/comments.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480012/boosts.json",
    "position": 3,
    "parent": {
      "id": 1069479829,
      "title": "To-dos",
      "type": "Todoset",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todosets/1069479829.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829"
    },
    "bucket": {
      "id": 2085958505,
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
      "created_at": "2026-05-28T17:22:22.069Z",
      "updated_at": "2026-07-21T00:05:55.167Z",
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
    "completed_ratio": "2/5",
    "name": "Strategy ideas",
    "color": null,
    "groups_url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069480012/groups.json",
    "todos_url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069480012/todos.json",
    "app_todos_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069480012/todos",
    "comments_app_url": "https://3.basecamp.com/195539477/buckets/2085958505/recordings/1069480012/comments"
  }
]
```
<!-- END GET /todosets/3/todolists.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/todosets/3/todolists.json
```


Get a to-do list
----------------

* `GET /todolists/2.json` will return the to-do list with an ID of `2`.

###### Example JSON Response
<!-- START GET /todolists/2.json -->
```json
{
  "id": 1069479863,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-04-16T23:22:00.000Z",
  "updated_at": "2026-07-21T01:05:29.822Z",
  "title": "Background and research",
  "inherits_status": true,
  "type": "Todolist",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479863.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479863",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg2Mz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--d86bbb914defcac2db83950d3e617035efd1f679.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479863/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479863/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479863/boosts.json",
  "position": 12,
  "parent": {
    "id": 1069479829,
    "title": "To-dos",
    "type": "Todoset",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todosets/1069479829.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829"
  },
  "bucket": {
    "id": 2085958505,
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
    "created_at": "2026-05-28T17:22:22.069Z",
    "updated_at": "2026-07-21T00:05:55.167Z",
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
  "completed_ratio": "1/5",
  "name": "Background and research",
  "color": "blue",
  "groups_url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479863/groups.json",
  "todos_url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479863/todos.json",
  "app_todos_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479863/todos",
  "comments_app_url": "https://3.basecamp.com/195539477/buckets/2085958505/recordings/1069479863/comments"
}
```
<!-- END GET /todolists/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/todolists/2.json
```


Create a to-do list
-------------------

* `POST /todosets/3/todolists.json` creates a to-do list under the to-do set with an ID of `3`.

**Required parameters**: `name` of the to-do list.

_Optional parameters_: `description` containing information about the to-do list. See our [Rich text guide][rich] for what HTML tags are allowed.

This endpoint will return `201 Created` with the current JSON representation of the to-do list if the creation was a success. See the [Get a to-do list](#get-a-to-do-list) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "name": "Launch",
  "description": "<div><em>Finish it!</em></div>"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"name":"Launch","description":"<div><em>Finish it!</em></div>"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/todosets/3/todolists.json
```


Update a to-do list
-------------------

* `PUT /todolists/2.json` allows changing the name and description of the to-do list with an ID of `2`.

This endpoint will return `200 OK` with the current JSON representation of the to-do list if the update was a success. See the [Get a to-do list](#get-a-to-do-list) endpoint for more info on the payload.

**Required parameters**: Pass all existing parameters in addition to those being updated. Omitting a parameter will clear its value.

* `name` of the to-do list. This one is always required, it can't be omitted as it can't be blank.

* `description` containing information about the to-do list. See our [Rich text guide][rich] for what HTML tags are allowed.

###### Example JSON Request

```json
{
  "name": "Relaunch",
  "description": "<div><strong>Try this again.</strong></div>"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"name":"Relaunch","description":"<div><strong>Try this again.</strong></div>"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/todolists/2.json
```



Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/todosets/3/todolists.json` → [Get to-do lists](#get-to-do-lists)
* `GET /buckets/1/todolists/2.json` → [Get a to-do list](#get-a-to-do-list)
* `POST /buckets/1/todosets/3/todolists.json` → [Create a to-do list](#create-a-to-do-list)
* `PUT /buckets/1/todolists/2.json` → [Update a to-do list](#update-a-to-do-list)

[trash]: recordings.md#trash-a-recording
[pagination]: ../README.md#pagination
[todoset]: todosets.md#get-to-do-set
[todos]: todos.md#to-dos
[rich]: rich_text.md
