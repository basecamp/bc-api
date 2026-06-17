Projects
=========

Endpoints:

- [Get all projects](#get-projects)
- [Get a project](#get-a-project)
- [Create a project](#create-a-project)
- [Update a project](#update-a-project)
- [Trash a project](#trash-a-project)

Get all projects
----------------

* `GET /projects.json` will return a [paginated list][pagination] of active projects visible to the current user sorted by most recently created project first.

_Optional parameters_:

* `status` - when set to `archived` or `trashed`, will return archived or trashed projects visible to the current user.

###### Example JSON Response
<!-- START GET /projects.json -->
```json
[
  {
    "id": 2085958504,
    "status": "active",
    "created_at": "2025-12-29T18:52:00.000Z",
    "updated_at": "2026-02-26T16:42:05.843Z",
    "name": "The Leto Laptop",
    "description": "Laptop product launch.",
    "purpose": "topic",
    "clients_enabled": false,
    "timesheet_enabled": true,
    "color": null,
    "last_needle_color": "green",
    "last_needle_position": null,
    "previous_needle_position": null,
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--63c6529d88eaffe640cc1ca84888819d8d327108.json",
    "url": "https://3.basecampapi.com/195539477/projects/2085958504.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958504",
    "dock": [
      {
        "id": 1069479392,
        "title": "Message Board",
        "name": "message_board",
        "enabled": true,
        "position": 1,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/message_boards/1069479392.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/message_boards/1069479392"
      },
      {
        "id": 1069479393,
        "title": "To-dos",
        "name": "todoset",
        "enabled": true,
        "position": 2,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todosets/1069479393.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todosets/1069479393"
      },
      {
        "id": 1069479394,
        "title": "Docs & Files",
        "name": "vault",
        "enabled": true,
        "position": 3,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/vaults/1069479394.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/vaults/1069479394"
      },
      {
        "id": 1069479395,
        "title": "Chat",
        "name": "chat",
        "enabled": true,
        "position": 4,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/chats/1069479395.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/chats/1069479395"
      },
      {
        "id": 1069479396,
        "title": "Schedule",
        "name": "schedule",
        "enabled": true,
        "position": 5,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/schedules/1069479396.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/schedules/1069479396"
      },
      {
        "id": 1069479397,
        "title": "Automatic Check-ins",
        "name": "questionnaire",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/questionnaires/1069479397.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/questionnaires/1069479397"
      },
      {
        "id": 1069479398,
        "title": "Email Forwards",
        "name": "inbox",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/inboxes/1069479398.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/inboxes/1069479398"
      },
      {
        "id": 1069479399,
        "title": "Card Table",
        "name": "kanban_board",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069479399.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069479399"
      }
    ],
    "bookmarked": false
  },
  {
    "id": 2085958505,
    "status": "active",
    "created_at": "2025-12-29T18:09:00.000Z",
    "updated_at": "2026-02-26T16:29:39.623Z",
    "name": "The Leto Locator",
    "description": "New software and hardware built for locating and securing Leto products.",
    "purpose": "topic",
    "clients_enabled": false,
    "timesheet_enabled": false,
    "color": null,
    "last_needle_color": "green",
    "last_needle_position": null,
    "previous_needle_position": null,
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--427e605de283e100f75da40006030176fd863024.json",
    "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958505",
    "client_company": {
      "id": 1033447818,
      "name": "Leto Brand"
    },
    "clientside": {
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/client/board.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/client/board"
    },
    "dock": [
      {
        "id": 1069479606,
        "title": "Message Board",
        "name": "message_board",
        "enabled": true,
        "position": 1,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/message_boards/1069479606.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/message_boards/1069479606"
      },
      {
        "id": 1069479607,
        "title": "To-dos",
        "name": "todoset",
        "enabled": true,
        "position": 2,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todosets/1069479607.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479607"
      },
      {
        "id": 1069479608,
        "title": "Docs & Files",
        "name": "vault",
        "enabled": true,
        "position": 3,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/vaults/1069479608.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/vaults/1069479608"
      },
      {
        "id": 1069479609,
        "title": "Chat",
        "name": "chat",
        "enabled": true,
        "position": 4,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/chats/1069479609.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/chats/1069479609"
      },
      {
        "id": 1069479610,
        "title": "Schedule",
        "name": "schedule",
        "enabled": true,
        "position": 5,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/schedules/1069479610.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/schedules/1069479610"
      },
      {
        "id": 1069479611,
        "title": "Automatic Check-ins",
        "name": "questionnaire",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/questionnaires/1069479611.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/questionnaires/1069479611"
      },
      {
        "id": 1069479612,
        "title": "Email Forwards",
        "name": "inbox",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/inboxes/1069479612.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/inboxes/1069479612"
      },
      {
        "id": 1069479613,
        "title": "Card Table",
        "name": "kanban_board",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/1069479613.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/1069479613"
      }
    ],
    "bookmarked": false
  }
]
```
<!-- END GET /projects.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/projects.json
```


Get a project
--------------

* `GET /projects/1.json` will return the project with the given ID, granted they have access to it.

The `dock` key contains an array of the current tools for this project. The `enabled` flag will be `true` if the tool is turned on for use. You can use the `url` parameter from each tool to jump to the resources available inside of this project.

###### Example JSON Response
<!-- START GET /projects/1.json -->
```json
{
  "id": 2085958504,
  "status": "active",
  "created_at": "2025-12-29T18:52:00.000Z",
  "updated_at": "2026-02-26T16:42:09.611Z",
  "name": "The Leto Laptop",
  "description": "Laptop product launch.",
  "purpose": "topic",
  "clients_enabled": false,
  "timesheet_enabled": true,
  "color": null,
  "last_needle_color": "green",
  "last_needle_position": null,
  "previous_needle_position": null,
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--63c6529d88eaffe640cc1ca84888819d8d327108.json",
  "url": "https://3.basecampapi.com/195539477/projects/2085958504.json",
  "app_url": "https://3.basecamp.com/195539477/projects/2085958504",
  "dock": [
    {
      "id": 1069479392,
      "title": "Message Board",
      "name": "message_board",
      "enabled": true,
      "position": 1,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/message_boards/1069479392.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/message_boards/1069479392"
    },
    {
      "id": 1069479393,
      "title": "To-dos",
      "name": "todoset",
      "enabled": true,
      "position": 2,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todosets/1069479393.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todosets/1069479393"
    },
    {
      "id": 1069479394,
      "title": "Docs & Files",
      "name": "vault",
      "enabled": true,
      "position": 3,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/vaults/1069479394.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/vaults/1069479394"
    },
    {
      "id": 1069479395,
      "title": "Chat",
      "name": "chat",
      "enabled": true,
      "position": 4,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/chats/1069479395.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/chats/1069479395"
    },
    {
      "id": 1069479396,
      "title": "Schedule",
      "name": "schedule",
      "enabled": true,
      "position": 5,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/schedules/1069479396.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/schedules/1069479396"
    },
    {
      "id": 1069479397,
      "title": "Automatic Check-ins",
      "name": "questionnaire",
      "enabled": false,
      "position": null,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/questionnaires/1069479397.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/questionnaires/1069479397"
    },
    {
      "id": 1069479398,
      "title": "Email Forwards",
      "name": "inbox",
      "enabled": false,
      "position": null,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/inboxes/1069479398.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/inboxes/1069479398"
    },
    {
      "id": 1069479399,
      "title": "Card Table",
      "name": "kanban_board",
      "enabled": false,
      "position": null,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069479399.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069479399"
    }
  ]
}
```
<!-- END GET /projects/1.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/projects/1.json
```


Create a project
-----------------

* `POST /projects.json` with at least a `name`, and optionally a `description`, to create a new project.

###### Example JSON Request

```json
{
  "name": "Marketing Campaign",
  "description": "For Client: Xyz Corp Conference"
}
```

This will return `201 Created` with the current JSON representation of the project if the creation was a success. See the [Get a project](#get-a-project) endpoint for more info. If the account is on a free subscription and you're trying to create a new project you'll see a `507 Insufficient Storage` and a response of:

```json
{
  "error": "The project limit for this account has been reached."
}
```

If you hit that error, the user will need to upgrade their subscription to any plan, which all have unlimited projects.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"name":"Marketing Campaign","description":"For Client: Xyz Corp Conference"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/projects.json
```


Update a project
-----------------

* `PUT /projects/1.json` will allow updating of a project's name and description.

**Required parameters**: `name` of the project.

_Optional parameters_:

* `description` - containing more information about the project.
* `schedule_attributes[start_date]` - project start date (ISO 8601). If provided also the end_date is
    required.
* `schedule_attributes[end_date]` - project end date (ISO 8601). If provided also the start_date is
    required.
* `admissions` - specifies access policy for a project within the same account. Available options
    are:
    * `invite` - only invited users can see the project.
    * `employee` - anyone from the account can see the project.
    * `team` - anyone from the account (except clients) can see the project.

###### Example JSON Request

```json
{
  "name": "Marketing Campaign",
  "description": "For Client: Xyz Corp Conference",
  "admissions": "team",
  "schedule_attributes": {
    "start_date": "2022-01-01",
    "end_date": "2022-04-01"
  }
}
```

This will return `200 OK` with the current JSON representation of the project if the update was a success. See the [Get a project](#get-a-project) endpoint for more info.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"name":"Marketing Campaign for Xyz Corp","description":"2016-2017 Strategy"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/2085958506.json
```


Trash a project
----------------

* `DELETE /projects/1.json` will mark the project with the given ID as trashed.

Trashed projects will be deleted from Basecamp 5 after 30 days. No parameters required. Returns `204 No Content` if successful.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/2085958507.json
```

[pagination]: ../README.md#pagination
