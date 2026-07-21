To-do sets
==========

All to-do lists under a project are children of a to-do set resource.

Endpoints:

- [Get to-do set](#get-to-do-set)


Get to-do set
-------------

* `GET /todosets/2.json` will return the to-do set with an ID of `2`.

To get the to-do set ID for a project, see the [Get a project][1] endpoint's `dock` payload. To retrieve its to-do lists, see the [Get to-do lists][2] endpoint.

###### Example JSON Response
<!-- START GET /todosets/2.json -->
```json
{
  "id": 1069479829,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-28T17:23:17.344Z",
  "updated_at": "2026-07-21T01:05:29.885Z",
  "title": "To-dos",
  "inherits_status": true,
  "type": "Todoset",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todosets/1069479829.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgyOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--983f8d107659f0cc1eb08dd65723367af62ad8e1.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479829/subscription.json",
  "position": 2,
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
  "completed": false,
  "completed_ratio": "16/64",
  "name": "To-dos",
  "todos_count": 2,
  "todolists_count": 10,
  "completed_loose_todos_count": 1,
  "todolists": [
    {
      "id": 1069480012,
      "title": "Strategy ideas",
      "description": null,
      "completed": false,
      "completed_ratio": "2/5",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069480012.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069480012"
    },
    {
      "id": 1069479950,
      "title": "Social stuff",
      "description": null,
      "completed": false,
      "completed_ratio": "8/17",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479950.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479950"
    },
    {
      "id": 1069479935,
      "title": "Chowder",
      "description": null,
      "completed": false,
      "completed_ratio": "0/3",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479935.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479935"
    },
    {
      "id": 1069479926,
      "title": "Android app",
      "description": null,
      "completed": false,
      "completed_ratio": "1/5",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479926.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479926"
    },
    {
      "id": 1069479919,
      "title": "iOS app",
      "description": null,
      "completed": false,
      "completed_ratio": "1/6",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479919.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479919"
    },
    {
      "id": 1069479914,
      "title": "Product page on company site",
      "description": null,
      "completed": false,
      "completed_ratio": "1/4",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479914.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479914"
    },
    {
      "id": 1069479904,
      "title": "Landing page + Microsite",
      "description": null,
      "completed": false,
      "completed_ratio": "0/5",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479904.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479904"
    },
    {
      "id": 1069479897,
      "title": "Promo video",
      "description": null,
      "completed": false,
      "completed_ratio": "1/6",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479897.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479897"
    },
    {
      "id": 1069479875,
      "title": "Product shots",
      "description": null,
      "completed": false,
      "completed_ratio": "0/5",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479875.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479875"
    },
    {
      "id": 1069479863,
      "title": "Background and research",
      "description": null,
      "completed": false,
      "completed_ratio": "1/5",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479863.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479863"
    }
  ],
  "todos_url": "https://3.basecampapi.com/195539477/buckets/2085958505/todosets/1069479829/todos.json",
  "app_todos_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829/todos",
  "hill_chart_url": "https://3.basecampapi.com/195539477/buckets/2085958505/todosets/1069479829/hill.json",
  "todolists_url": "https://3.basecampapi.com/195539477/buckets/2085958505/todosets/1069479829/todolists.json",
  "app_todoslists_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829/todolists"
}
```
<!-- END GET /todosets/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/todosets/2.json
```


Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/todosets/2.json` → [Get to-do set](#get-to-do-set)

[1]: projects.md#get-a-project
[2]: todolists.md#get-to-do-lists
[3]: recordings.md#trash-a-recording
