Projects
=========

Endpoints:

- [Get all projects](#get-projects)
- [Get a project](#get-a-project)
- [Get recent projects](#get-recent-projects)
- [Record a project visit](#record-a-project-visit)
- [Create a project](#create-a-project)
- [Update a project](#update-a-project)
- [Get project logo](#get-project-logo)
- [Update project logo](#update-project-logo)
- [Remove project logo](#remove-project-logo)
- [Get project wallpaper](#get-project-wallpaper)
- [Update project wallpaper](#update-project-wallpaper)
- [Remove project wallpaper](#remove-project-wallpaper)
- [Archive a project](#archive-a-project)
- [Unarchive a project](#unarchive-a-project)
- [Trash a project](#trash-a-project)

Get all projects
----------------

* `GET /projects.json` will return a [paginated list][pagination] of active projects visible to the current user sorted by most recently created project first. An agent's own token lists the projects the agent is in, with `bookmarked` and `starred` always `false`.

_Optional parameters_:

* `status` - set to `active`, `archived`, or `trashed` to filter projects by status.

Two flags describe the project's place on the current user's home page: `bookmarked` is `true` when the project is pinned there at all, whether starred or filed into a stack, and `starred` is `true` only when it carries a star.

###### Example JSON Response
<!-- START GET /projects.json -->
```json
[
  {
    "id": 2085958504,
    "status": "active",
    "created_at": "2026-07-29T18:30:00.000Z",
    "updated_at": "2026-09-12T08:21:50.481Z",
    "name": "The Leto Laptop",
    "description": "Laptop product launch.",
    "purpose": "topic",
    "clients_enabled": false,
    "timesheet_enabled": true,
    "color": null,
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--63c6529d88eaffe640cc1ca84888819d8d327108.json",
    "star_url": "https://3.basecampapi.com/195539477/buckets/2085958504/stars.json",
    "url": "https://3.basecampapi.com/195539477/projects/2085958504.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958504",
    "dock": [
      {
        "id": 1069479829,
        "title": "Message Board",
        "name": "message_board",
        "enabled": true,
        "position": 1,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/message_boards/1069479829.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/message_boards/1069479829"
      },
      {
        "id": 1069479830,
        "title": "To-dos",
        "name": "todoset",
        "enabled": true,
        "position": 2,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todosets/1069479830.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todosets/1069479830"
      },
      {
        "id": 1069479831,
        "title": "Docs & Files",
        "name": "vault",
        "enabled": true,
        "position": 3,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/vaults/1069479831.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/vaults/1069479831"
      },
      {
        "id": 1069479832,
        "title": "Calendar",
        "name": "schedule",
        "enabled": true,
        "position": 4,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/schedules/1069479832.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/schedules/1069479832"
      },
      {
        "id": 1069479833,
        "title": "Chat",
        "name": "chat",
        "enabled": true,
        "position": 5,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/chats/1069479833.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/chats/1069479833"
      },
      {
        "id": 1069479834,
        "title": "Card Table",
        "name": "kanban_board",
        "enabled": true,
        "position": 7,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069479834.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069479834"
      },
      {
        "id": 1069479840,
        "title": "Automatic Check-ins",
        "name": "questionnaire",
        "enabled": true,
        "position": 6,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/questionnaires/1069479840.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/questionnaires/1069479840"
      },
      {
        "id": 1069479841,
        "title": "Email Forwards",
        "name": "inbox",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/inboxes/1069479841.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/inboxes/1069479841"
      },
      {
        "id": 1069480307,
        "title": "Client onboarding",
        "name": "kanban_board",
        "enabled": true,
        "position": 8,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069480307.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069480307"
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
    "bookmarked": false,
    "starred": false
  },
  {
    "id": 2085958505,
    "status": "active",
    "created_at": "2026-07-29T17:16:00.000Z",
    "updated_at": "2026-09-12T08:19:06.771Z",
    "name": "The Leto Locator",
    "description": "New software and hardware built for locating and securing Leto products.",
    "purpose": "topic",
    "clients_enabled": false,
    "timesheet_enabled": false,
    "color": null,
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--427e605de283e100f75da40006030176fd863024.json",
    "star_url": "https://3.basecampapi.com/195539477/buckets/2085958505/stars.json",
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
        "id": 1069480049,
        "title": "Message Board",
        "name": "message_board",
        "enabled": true,
        "position": 1,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/message_boards/1069480049.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/message_boards/1069480049"
      },
      {
        "id": 1069480050,
        "title": "To-dos",
        "name": "todoset",
        "enabled": true,
        "position": 2,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todosets/1069480050.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069480050"
      },
      {
        "id": 1069480051,
        "title": "Docs & Files",
        "name": "vault",
        "enabled": true,
        "position": 3,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/vaults/1069480051.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/vaults/1069480051"
      },
      {
        "id": 1069480052,
        "title": "Calendar",
        "name": "schedule",
        "enabled": true,
        "position": 4,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/schedules/1069480052.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/schedules/1069480052"
      },
      {
        "id": 1069480053,
        "title": "Chat",
        "name": "chat",
        "enabled": true,
        "position": 5,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/chats/1069480053.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/chats/1069480053"
      },
      {
        "id": 1069480054,
        "title": "Card Table",
        "name": "kanban_board",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/1069480054.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/1069480054"
      },
      {
        "id": 1069480060,
        "title": "Automatic Check-ins",
        "name": "questionnaire",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/questionnaires/1069480060.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/questionnaires/1069480060"
      },
      {
        "id": 1069480061,
        "title": "Email Forwards",
        "name": "inbox",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/inboxes/1069480061.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/inboxes/1069480061"
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
    "bookmarked": false,
    "starred": false
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

`bookmarked` and `starred` reflect the current user's home page, as in [Get all projects](#get-projects).

Single-project responses include `logo` when the project has a logo, and omit it when there is none. It is not included in project lists or home responses. Its `url` requires authentication and redirects to the image file. The URL changes whenever the logo attachment is replaced:

```json
{
  "logo": {
    "url": "https://3.basecampapi.com/195539477/projects/2085958504/logo?v=957436214"
  }
}
```

Single-project responses include `wallpaper` when the project has a wallpaper. It is omitted when there is none, and is not included in project lists or home responses. Its `url` redirects to the image file, and changes whenever the wallpaper is replaced. Its `mode` is `fill` when the image fills the screen and `tile` when it repeats:

```json
"wallpaper": {
  "url": "https://3.basecampapi.com/195539477/projects/2085958504/wallpaper?v=1758000000",
  "mode": "tile"
}
```

###### Example JSON Response
<!-- START GET /projects/1.json -->
```json
{
  "id": 2085958504,
  "status": "active",
  "created_at": "2026-07-29T18:30:00.000Z",
  "updated_at": "2026-09-12T08:21:50.481Z",
  "name": "The Leto Laptop",
  "description": "Laptop product launch.",
  "purpose": "topic",
  "clients_enabled": false,
  "timesheet_enabled": true,
  "color": null,
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--63c6529d88eaffe640cc1ca84888819d8d327108.json",
  "star_url": "https://3.basecampapi.com/195539477/buckets/2085958504/stars.json",
  "url": "https://3.basecampapi.com/195539477/projects/2085958504.json",
  "app_url": "https://3.basecamp.com/195539477/projects/2085958504",
  "dock": [
    {
      "id": 1069479829,
      "title": "Message Board",
      "name": "message_board",
      "enabled": true,
      "position": 1,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/message_boards/1069479829.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/message_boards/1069479829"
    },
    {
      "id": 1069479830,
      "title": "To-dos",
      "name": "todoset",
      "enabled": true,
      "position": 2,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todosets/1069479830.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todosets/1069479830"
    },
    {
      "id": 1069479831,
      "title": "Docs & Files",
      "name": "vault",
      "enabled": true,
      "position": 3,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/vaults/1069479831.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/vaults/1069479831"
    },
    {
      "id": 1069479832,
      "title": "Calendar",
      "name": "schedule",
      "enabled": true,
      "position": 4,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/schedules/1069479832.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/schedules/1069479832"
    },
    {
      "id": 1069479833,
      "title": "Chat",
      "name": "chat",
      "enabled": true,
      "position": 5,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/chats/1069479833.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/chats/1069479833"
    },
    {
      "id": 1069479834,
      "title": "Card Table",
      "name": "kanban_board",
      "enabled": true,
      "position": 7,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069479834.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069479834"
    },
    {
      "id": 1069479840,
      "title": "Automatic Check-ins",
      "name": "questionnaire",
      "enabled": true,
      "position": 6,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/questionnaires/1069479840.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/questionnaires/1069479840"
    },
    {
      "id": 1069479841,
      "title": "Email Forwards",
      "name": "inbox",
      "enabled": false,
      "position": null,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/inboxes/1069479841.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/inboxes/1069479841"
    },
    {
      "id": 1069480307,
      "title": "Client onboarding",
      "name": "kanban_board",
      "enabled": true,
      "position": 8,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069480307.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069480307"
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
  "bookmarked": false,
  "starred": false
}
```
<!-- END GET /projects/1.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/projects/1.json
```


Get recent projects
-------------------

* `GET /my/recent_projects.json` will return the projects the current user has most recently visited, most recent visit first. Only active projects the user can still access are included, and the list is capped at the 50 most recent visits.

A visit is recorded when the user opens a project in Basecamp, when they create a project, and when an API client calls [Record a project visit](#record-a-project-visit). Each entry is the same shape as [Get a project](#get-a-project), plus `bookmarked`.

###### Example JSON Response
<!-- START GET /my/recent_projects.json -->
```json
[
  {
    "id": 2085958504,
    "status": "active",
    "created_at": "2026-07-29T18:30:00.000Z",
    "updated_at": "2026-09-12T08:21:50.481Z",
    "name": "The Leto Laptop",
    "description": "Laptop product launch.",
    "purpose": "topic",
    "clients_enabled": false,
    "timesheet_enabled": true,
    "color": null,
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--63c6529d88eaffe640cc1ca84888819d8d327108.json",
    "star_url": "https://3.basecampapi.com/195539477/buckets/2085958504/stars.json",
    "url": "https://3.basecampapi.com/195539477/projects/2085958504.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958504",
    "dock": [
      {
        "id": 1069479829,
        "title": "Message Board",
        "name": "message_board",
        "enabled": true,
        "position": 1,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/message_boards/1069479829.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/message_boards/1069479829"
      },
      {
        "id": 1069479830,
        "title": "To-dos",
        "name": "todoset",
        "enabled": true,
        "position": 2,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todosets/1069479830.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todosets/1069479830"
      },
      {
        "id": 1069479831,
        "title": "Docs & Files",
        "name": "vault",
        "enabled": true,
        "position": 3,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/vaults/1069479831.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/vaults/1069479831"
      },
      {
        "id": 1069479832,
        "title": "Calendar",
        "name": "schedule",
        "enabled": true,
        "position": 4,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/schedules/1069479832.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/schedules/1069479832"
      },
      {
        "id": 1069479833,
        "title": "Chat",
        "name": "chat",
        "enabled": true,
        "position": 5,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/chats/1069479833.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/chats/1069479833"
      },
      {
        "id": 1069479834,
        "title": "Card Table",
        "name": "kanban_board",
        "enabled": true,
        "position": 7,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069479834.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069479834"
      },
      {
        "id": 1069479840,
        "title": "Automatic Check-ins",
        "name": "questionnaire",
        "enabled": true,
        "position": 6,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/questionnaires/1069479840.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/questionnaires/1069479840"
      },
      {
        "id": 1069479841,
        "title": "Email Forwards",
        "name": "inbox",
        "enabled": false,
        "position": null,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/inboxes/1069479841.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/inboxes/1069479841"
      },
      {
        "id": 1069480307,
        "title": "Client onboarding",
        "name": "kanban_board",
        "enabled": true,
        "position": 8,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069480307.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069480307"
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
<!-- END GET /my/recent_projects.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/recent_projects.json
```


Record a project visit
----------------------

* `POST /projects/1/recent_visit.json` will record that the current user visited the project with the given ID, moving it to the front of [Get recent projects](#get-recent-projects).

No parameters required. Returns `204 No Content` if successful. Visits to archived or trashed projects are accepted but not recorded.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/2085958505/recent_visit.json
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
    * `invite` - only people added to the project have access. Account owners can also join it.
    * `employee` - team members and agents from the account's own company can join (not clients, agents added by a client or by someone since removed, or team members from other companies).
    * `team` - any team member or agent, except clients and agents added by a client or by someone since removed, can join.
* `wallpaper_mode` - how the project's wallpaper is displayed: `fill` to fill the screen, or `tile` to repeat it. To upload or remove the wallpaper itself, see [Update project wallpaper](#update-project-wallpaper) and [Remove project wallpaper](#remove-project-wallpaper).

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

A project's `status` is read-only here. Passing a `status` has no effect and still returns `200 OK`. To change it, see [Archive a project](#archive-a-project), [Unarchive a project](#unarchive-a-project), and [Trash a project](#trash-a-project).

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"name":"Marketing Campaign for Xyz Corp","description":"2016-2017 Strategy"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/2085958506.json
```


Get project logo
----------------

* `GET /projects/1/logo.json` will redirect to the logo image of the project with the given ID. People and agents who can read the project can use this endpoint, including those who cannot edit it. Requests must be authenticated. The same endpoint is available without the `.json` suffix, as returned by `logo.url`.

Returns `302 Found` with the image URL in the `Location` header, or `404 Not Found` when the project has no logo. Follow the redirect to download the image. Storage URLs expire, so request this endpoint again rather than reusing a saved storage URL.

Update project logo
-------------------

* `PUT /projects/1/logo.json` will upload or replace the logo of the project with the given ID. People and agents who can edit the project can use this endpoint. Readers without edit permission get `403 Forbidden`. Projects outside the caller's visibility return `404 Not Found`.

First [create a project](#create-a-project), then upload its logo using this endpoint. Logo upload is not supported as part of project creation. Logos use direct multipart file upload, not the `/attachments` flow or a signed global ID (SGID).

**Required parameters**:

* `logo` - the image file, sent as a multipart form upload. Accepted formats: PNG, JPEG, GIF, WebP, AVIF, HEIF, HEIC. Maximum file size: 5 MB (5,242,880 bytes). The existing server-side image validations used by the web app apply.

Returns `204 No Content` on success. Returns `422 Unprocessable Entity` with a JSON `error` message when the file is missing, is not a file upload, has an unsupported format, or exceeds the size limit. A rejected replacement leaves the existing logo unchanged. Other project fields are not changed by this endpoint.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -X PUT \
  -F "logo=@logo.png" \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/2085958504/logo.json
```

Remove project logo
-------------------

* `DELETE /projects/1/logo.json` will remove the logo of the project with the given ID. The same edit permission as [Update project logo](#update-project-logo) is required.

Returns `204 No Content`, including when the project had no logo. Subsequent single-project responses omit `logo`, and the logo download endpoint returns `404 Not Found`.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/2085958504/logo.json
```

Get project wallpaper
---------------------

* `GET /projects/1/wallpaper.json` will redirect to the wallpaper image of the project with the given ID. People and agents who can read the project can use this endpoint, including those who cannot edit it. Requests must be authenticated.

Returns `302 Found` with the image URL in the `Location` header. Returns `404 Not Found` when the project has no wallpaper.

Update project wallpaper
------------------------

* `PUT /projects/1/wallpaper.json` will upload or replace the wallpaper of the project with the given ID. People and agents who can edit the project can use this endpoint. Everyone else gets a `403 Forbidden`.

Project wallpapers use direct multipart file upload rather than the standard two-stage `/attachments` flow used elsewhere in the API.

**Required parameters**:

* `wallpaper` - the wallpaper image file, sent as a multipart form upload. Accepted formats: PNG, JPEG, GIF, WebP, AVIF, HEIF, HEIC. Maximum file size: 10 MB. The same server-side image validations used by the web app apply; the web file picker offers a narrower selection.

_Optional parameters_:

* `mode` - `fill` to fill the screen, or `tile` to repeat the image. Sent as a form field or in the query string. Leaving it out keeps the project's current mode.

Returns `204 No Content` on success. Returns `422 Unprocessable Entity` with an `error` message when the file is missing, the format is not accepted, the file exceeds 10 MB, or `mode` is neither `fill` nor `tile`.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -X PUT \
  -F "wallpaper=@wallpaper.png" \
  -F "mode=tile" \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/2085958506/wallpaper.json
```


Remove project wallpaper
------------------------

* `DELETE /projects/1/wallpaper.json` will remove the wallpaper of the project with the given ID. People and agents who can edit the project can use this endpoint. Everyone else gets a `403 Forbidden`.

Returns `204 No Content` on success, including when the project had no wallpaper.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/2085958506/wallpaper.json
```


Archive a project
------------------

* `PUT /projects/1/status/archived.json` will mark the project with the given ID as archived.

No parameters required. Returns `204 No Content` if successful. On accounts where archiving and trashing projects is limited to admins and the project's creator, everyone else gets a `403 Forbidden`. Accounts whose plan can't archive projects (`limits.can_archive_and_trash_projects` is `false`, see [Get account](account.md#get-account)) get a `403 Forbidden` too.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/2085958507/status/archived.json
```


Unarchive a project
--------------------

* `PUT /projects/1/status/active.json` will mark the project with the given ID as active, restoring it from either the archive or the trash.

No parameters required. Returns `204 No Content` if successful. If the account has reached its project limit you'll see a `507 Insufficient Storage` and the same response documented under [Create a project](#create-a-project); the project stays where it is until the subscription is upgraded.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/2085958507/status/active.json
```


Trash a project
----------------

* `DELETE /projects/1.json` will mark the project with the given ID as trashed.

Trashed projects will be deleted from Basecamp 5 after 30 days. No parameters required. Returns `204 No Content` if successful.

On accounts whose plan can't trash projects, the project is deleted permanently instead and can't be restored. The account's `limits.can_archive_and_trash_projects` says which applies; see [Get account](account.md#get-account).

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/2085958507.json
```

[pagination]: ../README.md#pagination
