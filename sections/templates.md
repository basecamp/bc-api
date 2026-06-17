Templates
=========

Endpoints:

- [Get Templates](#get-templates)
- [Get a Template](#get-a-template)
- [Create a Template](#create-a-template)
- [Update a Template](#update-a-template)
- [Trash a Template](#trash-a-template)
- [Create a Project Construction](#create-a-project-construction)
- [Get a Project Construction](#create-a-project-construction)

Get Templates
-------------

* `GET /templates.json` will return a [paginated list][pagination] of active Templates visible to the current user sorted by most recently created Template first.

_Optional parameters_:

* `status` - when set to `archived` or `trashed`, will return archived or trashed Templates visible to the current user.

###### Example JSON Response
<!-- START GET /templates.json -->
```json
[
  {
    "id": 2085958506,
    "status": "active",
    "created_at": "2026-02-12T06:55:56.041Z",
    "updated_at": "2026-02-12T06:13:55.432Z",
    "name": "Honcho Onboarding",
    "description": "Getting started on the right foot",
    "url": "https://3.basecampapi.com/195539477/templates/2085958506.json",
    "app_url": "https://3.basecamp.com/195539477/templates/2085958506",
    "dock": [
      {
        "id": 1069479712,
        "title": "Message Board",
        "name": "message_board",
        "enabled": true,
        "position": 1,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/message_boards/1069479712.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/message_boards/1069479712"
      },
      {
        "id": 1069479713,
        "title": "To-dos",
        "name": "todoset",
        "enabled": true,
        "position": 2,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/todosets/1069479713.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/todosets/1069479713"
      },
      {
        "id": 1069479714,
        "title": "Docs & Files",
        "name": "vault",
        "enabled": true,
        "position": 3,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/vaults/1069479714.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/vaults/1069479714"
      },
      {
        "id": 1069479715,
        "title": "Chat",
        "name": "chat",
        "enabled": true,
        "position": 4,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/chats/1069479715.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/chats/1069479715"
      },
      {
        "id": 1069479716,
        "title": "Schedule",
        "name": "schedule",
        "enabled": true,
        "position": 5,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/schedules/1069479716.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/schedules/1069479716"
      },
      {
        "id": 1069479717,
        "title": "Automatic Check-ins",
        "name": "questionnaire",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/questionnaires/1069479717.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/questionnaires/1069479717"
      },
      {
        "id": 1069479718,
        "title": "Email Forwards",
        "name": "inbox",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/inboxes/1069479718.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/inboxes/1069479718"
      },
      {
        "id": 1069479719,
        "title": "Card Table",
        "name": "kanban_board",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/card_tables/1069479719.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/card_tables/1069479719"
      }
    ]
  }
]
```
<!-- END GET /templates.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/templates.json
```

Get a Template
--------------

* `GET /templates/1.json` will return the Template with the given ID, granted they have access to it.

###### Example JSON Response
<!-- START GET /templates/1.json -->
```json
{
  "id": 2085958506,
  "status": "active",
  "created_at": "2026-02-12T06:55:56.041Z",
  "updated_at": "2026-02-12T06:13:55.432Z",
  "name": "Honcho Onboarding",
  "description": "Getting started on the right foot",
  "url": "https://3.basecampapi.com/195539477/templates/2085958506.json",
  "app_url": "https://3.basecamp.com/195539477/templates/2085958506",
  "dock": [
    {
      "id": 1069479712,
      "title": "Message Board",
      "name": "message_board",
      "enabled": true,
      "position": 1,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958506/message_boards/1069479712.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/message_boards/1069479712"
    },
    {
      "id": 1069479713,
      "title": "To-dos",
      "name": "todoset",
      "enabled": true,
      "position": 2,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958506/todosets/1069479713.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/todosets/1069479713"
    },
    {
      "id": 1069479714,
      "title": "Docs & Files",
      "name": "vault",
      "enabled": true,
      "position": 3,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958506/vaults/1069479714.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/vaults/1069479714"
    },
    {
      "id": 1069479715,
      "title": "Chat",
      "name": "chat",
      "enabled": true,
      "position": 4,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958506/chats/1069479715.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/chats/1069479715"
    },
    {
      "id": 1069479716,
      "title": "Schedule",
      "name": "schedule",
      "enabled": true,
      "position": 5,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958506/schedules/1069479716.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/schedules/1069479716"
    },
    {
      "id": 1069479717,
      "title": "Automatic Check-ins",
      "name": "questionnaire",
      "enabled": false,
      "position": null,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958506/questionnaires/1069479717.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/questionnaires/1069479717"
    },
    {
      "id": 1069479718,
      "title": "Email Forwards",
      "name": "inbox",
      "enabled": false,
      "position": null,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958506/inboxes/1069479718.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/inboxes/1069479718"
    },
    {
      "id": 1069479719,
      "title": "Card Table",
      "name": "kanban_board",
      "enabled": false,
      "position": null,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958506/card_tables/1069479719.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/card_tables/1069479719"
    }
  ]
}
```
<!-- END GET /templates/1.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/templates/1.json
```


Create a Template
-----------------

* `POST /templates.json` with at least a `name`, and optionally a `description`, to create a new Template.

###### Example JSON Request

```json
{
  "name": "New Starter Checklist",
  "description": "Things every new starter should do"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"name":"New Starter Checklist","description":"Things every new starter should do in their first week"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/templates.json
```

This will return `201 Created` with the current JSON representation of the Template if the creation was a success. See the [Get a Template](#get-a-template) endpoint for more info. Templates follow the same account limits as projects. If the account is on a free subscription and you're trying to create a new Template you'll see a `507 Insufficient Storage` and a response of:

```json
{
  "error": "The project/team limit for this account has been reached."
}
```

If you hit that error, the user will need to upgrade their subscription to any plan, which all have unlimited Templates.


Update a Template
-----------------

* `PUT /templates/1.json` will allow updating of a Template's name and description.

###### Example JSON Request

```json
{
  "name": "New Starter First Week Checklist",
  "description": "Things every new starter should do in their first week"
}
```

This will return `200 OK` with the current JSON representation of the Template if the update was a success. See the [Get a Template](#get-a-template) endpoint for more info.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"name":"New Starter First Week Checklist","description":"Things every new starter should do in their first week"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/templates/2085958506.json
```

Trash a Template
----------------

* `DELETE /templates/1.json` will mark the Template with the given ID as trashed.

Trashed Templates will be deleted from Basecamp 5 after 30 days. No parameters required. Returns `204 No Content` if successful.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/templates/2085958507.json
```


Create a Project Construction
--------------------------------

To create a project given a template, you need to create a project construction.

* `POST /templates/:template_id/project_constructions.json` with at least a project `name`, and optionally a `description`.

###### Example JSON Request

```json
{
  "project": {
    "name": "Marketing ",
    "description": "2016-2017 Strategy"
  }
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" -d '{"project":{"name":"Marketing Campaign","description":"For Client: Xyz Corp Conference"}}' -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/templates/2085958507/project_constructions.json
```


If creation was successful, this returns `201 Created` along with the current JSON representation of the project construction.

<!-- START POST /templates/1/project_constructions.json -->
```json
{
  "id": 598194961,
  "status": "pending",
  "url": "https://3.basecampapi.com/195539477/templates/2085958506/project_constructions/598194961.json"
}
```
<!-- END POST /templates/1/project_constructions.json -->

Get a Project Construction
--------------------------------

* `GET /templates/1/project_constructions/2.json` will return the project construction with an ID of `2` for the template with an ID of `1`.

This endpoint can be polled at regular intervals (no more than once a second) to see when construction is complete. When complete, the construction will have a status of "completed" and will provide information about the newly-created project:

<!-- START GET /templates/1/project_constructions/1.json -->
```json
{
  "id": 598194961,
  "status": "completed",
  "url": "https://3.basecampapi.com/195539477/templates/2085958506/project_constructions/598194961.json",
  "project": {
    "id": 2085958511,
    "status": "active",
    "created_at": "2026-02-26T16:41:57.253Z",
    "updated_at": "2026-02-26T16:41:58.479Z",
    "name": "New project from template",
    "description": null,
    "purpose": "topic",
    "clients_enabled": false,
    "timesheet_enabled": false,
    "color": null,
    "last_needle_color": "green",
    "last_needle_position": null,
    "previous_needle_position": null,
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUxMT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--4dd18a896aa1964bb280ed1b699308f2ad4d20c0.json",
    "url": "https://3.basecampapi.com/195539477/projects/2085958511.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958511",
    "dock": [
      {
        "id": 1069479980,
        "title": "Message Board",
        "name": "message_board",
        "enabled": true,
        "position": 1,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958511/message_boards/1069479980.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958511/message_boards/1069479980"
      },
      {
        "id": 1069479981,
        "title": "To-dos",
        "name": "todoset",
        "enabled": true,
        "position": 2,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958511/todosets/1069479981.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958511/todosets/1069479981"
      },
      {
        "id": 1069479986,
        "title": "Docs & Files",
        "name": "vault",
        "enabled": true,
        "position": 3,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958511/vaults/1069479986.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958511/vaults/1069479986"
      },
      {
        "id": 1069479987,
        "title": "Chat",
        "name": "chat",
        "enabled": true,
        "position": 4,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958511/chats/1069479987.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958511/chats/1069479987"
      },
      {
        "id": 1069479988,
        "title": "Schedule",
        "name": "schedule",
        "enabled": true,
        "position": 5,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958511/schedules/1069479988.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958511/schedules/1069479988"
      },
      {
        "id": 1069479989,
        "title": "Automatic Check-ins",
        "name": "questionnaire",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958511/questionnaires/1069479989.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958511/questionnaires/1069479989"
      },
      {
        "id": 1069479990,
        "title": "Email Forwards",
        "name": "inbox",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958511/inboxes/1069479990.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958511/inboxes/1069479990"
      },
      {
        "id": 1069479991,
        "title": "Card Table",
        "name": "kanban_board",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958511/card_tables/1069479991.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958511/card_tables/1069479991"
      }
    ]
  }
}
```
<!-- END GET /templates/1/project_constructions/1.json -->

[pagination]: ../README.md#pagination
