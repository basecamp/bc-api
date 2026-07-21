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
    "id": 2085958505,
    "status": "active",
    "created_at": "2026-04-13T20:24:00.000Z",
    "updated_at": "2026-07-21T01:05:29.829Z",
    "name": "The Leto Laptop",
    "description": "Laptop product launch.",
    "purpose": "topic",
    "clients_enabled": false,
    "timesheet_enabled": true,
    "color": null,
    "last_needle_color": "yellow",
    "last_needle_position": 42,
    "previous_needle_position": null,
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--427e605de283e100f75da40006030176fd863024.json",
    "star_url": "https://3.basecampapi.com/195539477/buckets/2085958505/stars.json",
    "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958505",
    "dock": [
      {
        "id": 1069479828,
        "title": "Message Board",
        "name": "message_board",
        "enabled": true,
        "position": 1,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/message_boards/1069479828.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/message_boards/1069479828"
      },
      {
        "id": 1069479829,
        "title": "To-dos",
        "name": "todoset",
        "enabled": true,
        "position": 2,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todosets/1069479829.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829"
      },
      {
        "id": 1069479830,
        "title": "Docs & Files",
        "name": "vault",
        "enabled": true,
        "position": 3,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/vaults/1069479830.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/vaults/1069479830"
      },
      {
        "id": 1069479831,
        "title": "Calendar",
        "name": "schedule",
        "enabled": true,
        "position": 4,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/schedules/1069479831.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/schedules/1069479831"
      },
      {
        "id": 1069479832,
        "title": "Chat",
        "name": "chat",
        "enabled": true,
        "position": 5,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/chats/1069479832.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/chats/1069479832"
      },
      {
        "id": 1069479833,
        "title": "Card Table",
        "name": "kanban_board",
        "enabled": true,
        "position": 7,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/1069479833.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/1069479833"
      },
      {
        "id": 1069479839,
        "title": "Automatic Check-ins",
        "name": "questionnaire",
        "enabled": true,
        "position": 6,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/questionnaires/1069479839.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/questionnaires/1069479839"
      },
      {
        "id": 1069479840,
        "title": "Email Forwards",
        "name": "inbox",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/inboxes/1069479840.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/inboxes/1069479840"
      }
    ],
    "people": {
      "team": {
        "count": 8,
        "sample": [
          {
            "id": 1049715938,
            "name": "Annie Bryan",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOJkkT4=--732a71fbd28ec10d9bf4466abd3588a8bea40bdb/avatar"
          },
          {
            "id": 1049715939,
            "name": "Cheryl Walters",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBONkkT4=--b57b5a44335d4c3ba1a2585abd6e5c7e4c85fdd6/avatar"
          },
          {
            "id": 1049715940,
            "name": "Jared Davis",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBORkkT4=--2667d9ced3ec021946197cbb6c3083f0f95f3b6a/avatar"
          },
          {
            "id": 1049715941,
            "name": "Jennifer Hemmersmith Young",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOVkkT4=--33e3fc268c87411378691c71b6f13658e0b40967/avatar"
          },
          {
            "id": 1049715942,
            "name": "Josh Fiske",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOZkkT4=--b8553b154990a1112ab6275b749296c4a3b56334/avatar"
          },
          {
            "id": 1049715943,
            "name": "Nicole Katz",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOdkkT4=--1d2b80e583133f93afe008f88166b674fc0287a4/avatar"
          },
          {
            "id": 1049715944,
            "name": "Steve Marsh",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOhkkT4=--b169e35b345bcc26eca6964b7ef7de2c16b6f238/avatar"
          },
          {
            "id": 1049715913,
            "name": "Victor Cooper",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
          }
        ]
      }
    },
    "all_access": false,
    "bookmarked": false
  },
  {
    "id": 2085958506,
    "status": "active",
    "created_at": "2026-04-13T15:45:00.000Z",
    "updated_at": "2026-07-20T04:05:52.507Z",
    "name": "The Leto Locator",
    "description": "New software and hardware built for locating and securing Leto products.",
    "purpose": "topic",
    "clients_enabled": false,
    "timesheet_enabled": false,
    "color": null,
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwNj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--c1f4e47bbc088a5055d422c816957a763ed42aec.json",
    "star_url": "https://3.basecampapi.com/195539477/buckets/2085958506/stars.json",
    "url": "https://3.basecampapi.com/195539477/projects/2085958506.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958506",
    "client_company": {
      "id": 1033447818,
      "name": "Leto Brand"
    },
    "clientside": {
      "url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/board.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/client/board"
    },
    "dock": [
      {
        "id": 1069480045,
        "title": "Message Board",
        "name": "message_board",
        "enabled": true,
        "position": 1,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/message_boards/1069480045.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/message_boards/1069480045"
      },
      {
        "id": 1069480046,
        "title": "To-dos",
        "name": "todoset",
        "enabled": true,
        "position": 2,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/todosets/1069480046.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/todosets/1069480046"
      },
      {
        "id": 1069480047,
        "title": "Docs & Files",
        "name": "vault",
        "enabled": true,
        "position": 3,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/vaults/1069480047.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/vaults/1069480047"
      },
      {
        "id": 1069480048,
        "title": "Calendar",
        "name": "schedule",
        "enabled": true,
        "position": 4,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/schedules/1069480048.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/schedules/1069480048"
      },
      {
        "id": 1069480049,
        "title": "Chat",
        "name": "chat",
        "enabled": true,
        "position": 5,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/chats/1069480049.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/chats/1069480049"
      },
      {
        "id": 1069480050,
        "title": "Card Table",
        "name": "kanban_board",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/card_tables/1069480050.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/card_tables/1069480050"
      },
      {
        "id": 1069480056,
        "title": "Automatic Check-ins",
        "name": "questionnaire",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/questionnaires/1069480056.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/questionnaires/1069480056"
      },
      {
        "id": 1069480057,
        "title": "Email Forwards",
        "name": "inbox",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/inboxes/1069480057.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/inboxes/1069480057"
      }
    ],
    "people": {
      "team": {
        "count": 8,
        "sample": [
          {
            "id": 1049715938,
            "name": "Annie Bryan",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOJkkT4=--732a71fbd28ec10d9bf4466abd3588a8bea40bdb/avatar"
          },
          {
            "id": 1049715939,
            "name": "Cheryl Walters",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBONkkT4=--b57b5a44335d4c3ba1a2585abd6e5c7e4c85fdd6/avatar"
          },
          {
            "id": 1049715940,
            "name": "Jared Davis",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBORkkT4=--2667d9ced3ec021946197cbb6c3083f0f95f3b6a/avatar"
          },
          {
            "id": 1049715941,
            "name": "Jennifer Hemmersmith Young",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOVkkT4=--33e3fc268c87411378691c71b6f13658e0b40967/avatar"
          },
          {
            "id": 1049715942,
            "name": "Josh Fiske",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOZkkT4=--b8553b154990a1112ab6275b749296c4a3b56334/avatar"
          },
          {
            "id": 1049715943,
            "name": "Nicole Katz",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOdkkT4=--1d2b80e583133f93afe008f88166b674fc0287a4/avatar"
          },
          {
            "id": 1049715944,
            "name": "Steve Marsh",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOhkkT4=--b169e35b345bcc26eca6964b7ef7de2c16b6f238/avatar"
          },
          {
            "id": 1049715913,
            "name": "Victor Cooper",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
          }
        ]
      }
    },
    "all_access": false,
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
  "id": 2085958505,
  "status": "active",
  "created_at": "2026-04-13T20:24:00.000Z",
  "updated_at": "2026-07-21T01:05:29.829Z",
  "name": "The Leto Laptop",
  "description": "Laptop product launch.",
  "purpose": "topic",
  "clients_enabled": false,
  "timesheet_enabled": true,
  "color": null,
  "last_needle_color": "yellow",
  "last_needle_position": 42,
  "previous_needle_position": null,
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--427e605de283e100f75da40006030176fd863024.json",
  "star_url": "https://3.basecampapi.com/195539477/buckets/2085958505/stars.json",
  "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
  "app_url": "https://3.basecamp.com/195539477/projects/2085958505",
  "dock": [
    {
      "id": 1069479828,
      "title": "Message Board",
      "name": "message_board",
      "enabled": true,
      "position": 1,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/message_boards/1069479828.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/message_boards/1069479828"
    },
    {
      "id": 1069479829,
      "title": "To-dos",
      "name": "todoset",
      "enabled": true,
      "position": 2,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todosets/1069479829.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829"
    },
    {
      "id": 1069479830,
      "title": "Docs & Files",
      "name": "vault",
      "enabled": true,
      "position": 3,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/vaults/1069479830.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/vaults/1069479830"
    },
    {
      "id": 1069479831,
      "title": "Calendar",
      "name": "schedule",
      "enabled": true,
      "position": 4,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/schedules/1069479831.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/schedules/1069479831"
    },
    {
      "id": 1069479832,
      "title": "Chat",
      "name": "chat",
      "enabled": true,
      "position": 5,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/chats/1069479832.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/chats/1069479832"
    },
    {
      "id": 1069479833,
      "title": "Card Table",
      "name": "kanban_board",
      "enabled": true,
      "position": 7,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/1069479833.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/1069479833"
    },
    {
      "id": 1069479839,
      "title": "Automatic Check-ins",
      "name": "questionnaire",
      "enabled": true,
      "position": 6,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/questionnaires/1069479839.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/questionnaires/1069479839"
    },
    {
      "id": 1069479840,
      "title": "Email Forwards",
      "name": "inbox",
      "enabled": false,
      "position": null,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/inboxes/1069479840.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/inboxes/1069479840"
    }
  ],
  "people": {
    "team": {
      "count": 8,
      "sample": [
        {
          "id": 1049715938,
          "name": "Annie Bryan",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOJkkT4=--732a71fbd28ec10d9bf4466abd3588a8bea40bdb/avatar"
        },
        {
          "id": 1049715939,
          "name": "Cheryl Walters",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBONkkT4=--b57b5a44335d4c3ba1a2585abd6e5c7e4c85fdd6/avatar"
        },
        {
          "id": 1049715940,
          "name": "Jared Davis",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBORkkT4=--2667d9ced3ec021946197cbb6c3083f0f95f3b6a/avatar"
        },
        {
          "id": 1049715941,
          "name": "Jennifer Hemmersmith Young",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOVkkT4=--33e3fc268c87411378691c71b6f13658e0b40967/avatar"
        },
        {
          "id": 1049715942,
          "name": "Josh Fiske",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOZkkT4=--b8553b154990a1112ab6275b749296c4a3b56334/avatar"
        },
        {
          "id": 1049715943,
          "name": "Nicole Katz",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOdkkT4=--1d2b80e583133f93afe008f88166b674fc0287a4/avatar"
        },
        {
          "id": 1049715944,
          "name": "Steve Marsh",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOhkkT4=--b169e35b345bcc26eca6964b7ef7de2c16b6f238/avatar"
        },
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
