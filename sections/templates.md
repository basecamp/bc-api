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
    "id": 2085958507,
    "status": "active",
    "created_at": "2026-05-28T17:57:35.453Z",
    "updated_at": "2026-05-28T17:23:35.840Z",
    "name": "Honcho Onboarding",
    "description": "Getting started on the right foot",
    "url": "https://3.basecampapi.com/195539477/templates/2085958507.json",
    "app_url": "https://3.basecamp.com/195539477/templates/2085958507",
    "dock": [
      {
        "id": 1069480151,
        "title": "Message Board",
        "name": "message_board",
        "enabled": true,
        "position": 1,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958507/message_boards/1069480151.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/message_boards/1069480151"
      },
      {
        "id": 1069480152,
        "title": "To-dos",
        "name": "todoset",
        "enabled": true,
        "position": 2,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958507/todosets/1069480152.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/todosets/1069480152"
      },
      {
        "id": 1069480153,
        "title": "Docs & Files",
        "name": "vault",
        "enabled": true,
        "position": 3,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958507/vaults/1069480153.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/vaults/1069480153"
      },
      {
        "id": 1069480154,
        "title": "Calendar",
        "name": "schedule",
        "enabled": true,
        "position": 4,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958507/schedules/1069480154.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/schedules/1069480154"
      },
      {
        "id": 1069480155,
        "title": "Chat",
        "name": "chat",
        "enabled": true,
        "position": 5,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958507/chats/1069480155.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/chats/1069480155"
      },
      {
        "id": 1069480156,
        "title": "Card Table",
        "name": "kanban_board",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958507/card_tables/1069480156.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/card_tables/1069480156"
      },
      {
        "id": 1069480162,
        "title": "Automatic Check-ins",
        "name": "questionnaire",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958507/questionnaires/1069480162.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/questionnaires/1069480162"
      },
      {
        "id": 1069480163,
        "title": "Email Forwards",
        "name": "inbox",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958507/inboxes/1069480163.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/inboxes/1069480163"
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
  "id": 2085958507,
  "status": "active",
  "created_at": "2026-05-28T17:57:35.453Z",
  "updated_at": "2026-05-28T17:23:35.840Z",
  "name": "Honcho Onboarding",
  "description": "Getting started on the right foot",
  "url": "https://3.basecampapi.com/195539477/templates/2085958507.json",
  "app_url": "https://3.basecamp.com/195539477/templates/2085958507",
  "dock": [
    {
      "id": 1069480151,
      "title": "Message Board",
      "name": "message_board",
      "enabled": true,
      "position": 1,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958507/message_boards/1069480151.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/message_boards/1069480151"
    },
    {
      "id": 1069480152,
      "title": "To-dos",
      "name": "todoset",
      "enabled": true,
      "position": 2,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958507/todosets/1069480152.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/todosets/1069480152"
    },
    {
      "id": 1069480153,
      "title": "Docs & Files",
      "name": "vault",
      "enabled": true,
      "position": 3,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958507/vaults/1069480153.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/vaults/1069480153"
    },
    {
      "id": 1069480154,
      "title": "Calendar",
      "name": "schedule",
      "enabled": true,
      "position": 4,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958507/schedules/1069480154.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/schedules/1069480154"
    },
    {
      "id": 1069480155,
      "title": "Chat",
      "name": "chat",
      "enabled": true,
      "position": 5,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958507/chats/1069480155.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/chats/1069480155"
    },
    {
      "id": 1069480156,
      "title": "Card Table",
      "name": "kanban_board",
      "enabled": false,
      "position": null,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958507/card_tables/1069480156.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/card_tables/1069480156"
    },
    {
      "id": 1069480162,
      "title": "Automatic Check-ins",
      "name": "questionnaire",
      "enabled": false,
      "position": null,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958507/questionnaires/1069480162.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/questionnaires/1069480162"
    },
    {
      "id": 1069480163,
      "title": "Email Forwards",
      "name": "inbox",
      "enabled": false,
      "position": null,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958507/inboxes/1069480163.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958507/inboxes/1069480163"
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
  "id": 598194962,
  "status": "pending",
  "url": "https://3.basecampapi.com/195539477/templates/2085958507/project_constructions/598194962.json"
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
  "id": 598194962,
  "status": "completed",
  "url": "https://3.basecampapi.com/195539477/templates/2085958507/project_constructions/598194962.json",
  "project": {
    "id": 2085958514,
    "status": "active",
    "created_at": "2026-07-21T01:05:45.318Z",
    "updated_at": "2026-07-21T01:05:47.276Z",
    "name": "New project from template",
    "description": null,
    "purpose": "topic",
    "clients_enabled": false,
    "timesheet_enabled": false,
    "color": null,
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUxND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--a1c8688229bb9e8800d90081f361eeca435d324b.json",
    "star_url": "https://3.basecampapi.com/195539477/buckets/2085958514/stars.json",
    "url": "https://3.basecampapi.com/195539477/projects/2085958514.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958514",
    "dock": [
      {
        "id": 1069480412,
        "title": "Message Board",
        "name": "message_board",
        "enabled": true,
        "position": 1,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958514/message_boards/1069480412.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/message_boards/1069480412"
      },
      {
        "id": 1069480413,
        "title": "To-dos",
        "name": "todoset",
        "enabled": true,
        "position": 2,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958514/todosets/1069480413.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/todosets/1069480413"
      },
      {
        "id": 1069480418,
        "title": "Docs & Files",
        "name": "vault",
        "enabled": true,
        "position": 3,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958514/vaults/1069480418.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/vaults/1069480418"
      },
      {
        "id": 1069480419,
        "title": "Calendar",
        "name": "schedule",
        "enabled": true,
        "position": 4,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958514/schedules/1069480419.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/schedules/1069480419"
      },
      {
        "id": 1069480420,
        "title": "Chat",
        "name": "chat",
        "enabled": true,
        "position": 5,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958514/chats/1069480420.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/chats/1069480420"
      },
      {
        "id": 1069480421,
        "title": "Card Table",
        "name": "kanban_board",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958514/card_tables/1069480421.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/card_tables/1069480421"
      },
      {
        "id": 1069480428,
        "title": "Automatic Check-ins",
        "name": "questionnaire",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958514/questionnaires/1069480428.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/questionnaires/1069480428"
      },
      {
        "id": 1069480429,
        "title": "Email Forwards",
        "name": "inbox",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958514/inboxes/1069480429.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/inboxes/1069480429"
      }
    ],
    "people": {
      "team": {
        "count": 1,
        "sample": [
          {
            "id": 1049715913,
            "name": "Victor Cooper",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
          }
        ]
      }
    },
    "all_access": false
  }
}
```
<!-- END GET /templates/1/project_constructions/1.json -->

[pagination]: ../README.md#pagination
