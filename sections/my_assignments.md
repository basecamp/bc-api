My assignments
===============

Endpoints for retrieving the current user's assignments, including active assignments split by priority, completed assignments, and due assignments filtered by time scope.

Each assignment includes its content, type, bucket, parent, assignees, due dates, completion status, and any child assignments (e.g. card steps nested under their parent card).

**Note:** These endpoints return the full result set and are not paginated.

Endpoints:

- [Get assignments](#get-assignments)
- [Get completed assignments](#get-completed-assignments)
- [Get due assignments](#get-due-assignments)
- [Act on assignments](#act-on-assignments)
- [Prioritize an assignment](#prioritize-an-assignment)
- [Deprioritize an assignment](#deprioritize-an-assignment)
- [Reorder Up Next](#reorder-up-next)


Get assignments
---------------

* `GET /my/assignments.json` will return the current user's active assignments grouped into `priorities` and `non_priorities`. Card table steps are normalized to their parent card, with steps included as `children`.

###### Example JSON Response
<!-- START GET /my/assignments.json -->
```json
{
  "priorities": [],
  "non_priorities": [
    {
      "id": 1069479576,
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/todos/1069479576",
      "content": "Awards",
      "starts_on": null,
      "due_on": null,
      "bucket": {
        "id": 2085958502,
        "name": "Honcho Design Newsroom",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958502"
      },
      "completed": false,
      "type": "todo",
      "assignees": [
        {
          "id": 1049715913,
          "name": "Victor Cooper",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
        }
      ],
      "comments_count": 0,
      "has_description": false,
      "parent": {
        "id": 1069479563,
        "title": "Meetup setup",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/todolists/1069479563"
      },
      "children": []
    },
    {
      "id": 1069479711,
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958503/todos/1069479711",
      "content": "Mary Brown",
      "starts_on": null,
      "due_on": null,
      "bucket": {
        "id": 2085958503,
        "name": "Honcho Recruiting and Hiring",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958503"
      },
      "completed": false,
      "type": "todo",
      "assignees": [
        {
          "id": 1049715913,
          "name": "Victor Cooper",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
        }
      ],
      "comments_count": 0,
      "has_description": false,
      "parent": {
        "id": 1069479710,
        "title": "Phone screen",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958503/todolists/1069479710"
      },
      "children": []
    },
    {
      "id": 1069479712,
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958503/todos/1069479712",
      "content": "Lisa Larue",
      "starts_on": null,
      "due_on": null,
      "bucket": {
        "id": 2085958503,
        "name": "Honcho Recruiting and Hiring",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958503"
      },
      "completed": false,
      "type": "todo",
      "assignees": [
        {
          "id": 1049715913,
          "name": "Victor Cooper",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
        }
      ],
      "comments_count": 0,
      "has_description": false,
      "parent": {
        "id": 1069479710,
        "title": "Phone screen",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958503/todolists/1069479710"
      },
      "children": []
    },
    {
      "id": 1069479734,
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958503/todos/1069479734",
      "content": "Nancy Johnson",
      "starts_on": null,
      "due_on": null,
      "bucket": {
        "id": 2085958503,
        "name": "Honcho Recruiting and Hiring",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958503"
      },
      "completed": false,
      "type": "todo",
      "assignees": [
        {
          "id": 1049715913,
          "name": "Victor Cooper",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
        }
      ],
      "comments_count": 0,
      "has_description": false,
      "parent": {
        "id": 1069479723,
        "title": "First interview / Team",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958503/todolists/1069479723"
      },
      "children": []
    },
    {
      "id": 1069479736,
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958503/todos/1069479736",
      "content": "Carlotta Sheppard",
      "starts_on": null,
      "due_on": null,
      "bucket": {
        "id": 2085958503,
        "name": "Honcho Recruiting and Hiring",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958503"
      },
      "completed": false,
      "type": "todo",
      "assignees": [
        {
          "id": 1049715913,
          "name": "Victor Cooper",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
        }
      ],
      "comments_count": 0,
      "has_description": false,
      "parent": {
        "id": 1069479735,
        "title": "Second interview / Managers",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958503/todolists/1069479735"
      },
      "children": []
    },
    {
      "id": 1069479737,
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958503/todos/1069479737",
      "content": "Joanne Wilkerson",
      "starts_on": null,
      "due_on": null,
      "bucket": {
        "id": 2085958503,
        "name": "Honcho Recruiting and Hiring",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958503"
      },
      "completed": false,
      "type": "todo",
      "assignees": [
        {
          "id": 1049715913,
          "name": "Victor Cooper",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
        }
      ],
      "comments_count": 0,
      "has_description": false,
      "parent": {
        "id": 1069479735,
        "title": "Second interview / Managers",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958503/todolists/1069479735"
      },
      "children": []
    },
    {
      "id": 1069479738,
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958503/todos/1069479738",
      "content": "Greg Campbell",
      "starts_on": null,
      "due_on": null,
      "bucket": {
        "id": 2085958503,
        "name": "Honcho Recruiting and Hiring",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958503"
      },
      "completed": false,
      "type": "todo",
      "assignees": [
        {
          "id": 1049715913,
          "name": "Victor Cooper",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
        }
      ],
      "comments_count": 0,
      "has_description": false,
      "parent": {
        "id": 1069479735,
        "title": "Second interview / Managers",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958503/todolists/1069479735"
      },
      "children": []
    },
    {
      "id": 1069479801,
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todos/1069479801",
      "content": "Why isn't this done yet?",
      "starts_on": null,
      "due_on": "2026-05-25",
      "bucket": {
        "id": 2085958504,
        "name": "Honcho HQ",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504"
      },
      "completed": false,
      "type": "todo",
      "assignees": [
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
      ],
      "comments_count": 0,
      "has_description": false,
      "parent": {
        "id": 1069479800,
        "title": "Marketing Campaign: TV Ad",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todolists/1069479800"
      },
      "children": []
    },
    {
      "id": 1069479804,
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todos/1069479804",
      "content": "Render all Ad variants",
      "starts_on": "2026-06-11",
      "due_on": "2026-06-18",
      "bucket": {
        "id": 2085958504,
        "name": "Honcho HQ",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504"
      },
      "completed": false,
      "type": "todo",
      "assignees": [
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
      ],
      "comments_count": 0,
      "has_description": false,
      "parent": {
        "id": 1069479800,
        "title": "Marketing Campaign: TV Ad",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todolists/1069479800"
      },
      "children": []
    },
    {
      "id": 1069479861,
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todos/1069479861",
      "content": "Make to-do lists",
      "starts_on": null,
      "due_on": "2026-05-29",
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505"
      },
      "completed": false,
      "type": "todo",
      "assignees": [
        {
          "id": 1049715913,
          "name": "Victor Cooper",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
        }
      ],
      "comments_count": 0,
      "has_description": false,
      "parent": {
        "id": 1069479829,
        "title": "To-dos",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829"
      },
      "children": []
    }
  ]
}
```
<!-- END GET /my/assignments.json -->

Assignments with card table steps are normalized so the parent card appears as the top-level item with its steps nested as `children`. Priority items include a `priority_recording_id` field.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/assignments.json
```


Get completed assignments
-------------------------

* `GET /my/assignments/completed.json` will return the current user's completed assignments. Archived and trashed recordings are excluded.

###### Example JSON Response
<!-- START GET /my/assignments/completed.json -->
```json
[
  {
    "id": 1069480405,
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todos/1069480405",
    "content": "Confirm the launch-party caterer",
    "starts_on": null,
    "due_on": null,
    "bucket": {
      "id": 2085958505,
      "name": "The Leto Laptop",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505"
    },
    "completed": true,
    "type": "todo",
    "assignees": [
      {
        "id": 1049715913,
        "name": "Victor Cooper",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
      }
    ],
    "comments_count": 0,
    "has_description": false,
    "parent": {
      "id": 1069479863,
      "title": "Background and research",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479863"
    },
    "children": []
  }
]
```
<!-- END GET /my/assignments/completed.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/assignments/completed.json
```


Get due assignments
-------------------

* `GET /my/assignments/due.json` will return the current user's assignments filtered by due date scope. Defaults to `overdue` when no scope is provided.

_Optional parameters_:

* `scope` - filter by due date range. Valid options: `overdue`, `due_today`, `due_tomorrow`, `due_later_this_week`, `due_next_week`, `due_later`.

Providing an invalid `scope` returns `400 Bad Request` with an error listing the valid options:

```json
{
  "error": "Invalid scope 'invalid'. Valid options: overdue, due_today, due_tomorrow, due_later_this_week, due_next_week, due_later"
}
```

###### Example JSON Response
<!-- START GET /my/assignments/due.json -->
```json
[
  {
    "id": 1069479801,
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todos/1069479801",
    "content": "Why isn't this done yet?",
    "starts_on": null,
    "due_on": "2026-05-25",
    "bucket": {
      "id": 2085958504,
      "name": "Honcho HQ",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504"
    },
    "completed": false,
    "type": "todo",
    "assignees": [
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
    ],
    "comments_count": 0,
    "has_description": false,
    "parent": {
      "id": 1069479800,
      "title": "Marketing Campaign: TV Ad",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todolists/1069479800"
    },
    "children": []
  },
  {
    "id": 1069479861,
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todos/1069479861",
    "content": "Make to-do lists",
    "starts_on": null,
    "due_on": "2026-05-29",
    "bucket": {
      "id": 2085958505,
      "name": "The Leto Laptop",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505"
    },
    "completed": false,
    "type": "todo",
    "assignees": [
      {
        "id": 1049715913,
        "name": "Victor Cooper",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
      }
    ],
    "comments_count": 0,
    "has_description": false,
    "parent": {
      "id": 1069479829,
      "title": "To-dos",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829"
    },
    "children": []
  },
  {
    "id": 1069479804,
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todos/1069479804",
    "content": "Render all Ad variants",
    "starts_on": "2026-06-11",
    "due_on": "2026-06-18",
    "bucket": {
      "id": 2085958504,
      "name": "Honcho HQ",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504"
    },
    "completed": false,
    "type": "todo",
    "assignees": [
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
    ],
    "comments_count": 0,
    "has_description": false,
    "parent": {
      "id": 1069479800,
      "title": "Marketing Campaign: TV Ad",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todolists/1069479800"
    },
    "children": []
  }
]
```
<!-- END GET /my/assignments/due.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/assignments/due.json?scope=overdue
```


Act on assignments
------------------

Assignments are created and changed through the to-do, card, and card table step endpoints, not through `/my/assignments`. A card table step is returned nested under its parent card as a `children` entry, and it's acted on through its own step endpoints, not the parent card's:

* **Assign or unassign** — pass `assignee_ids` when updating a [to-do](todos.md#update-a-to-do) or a [card](card_table_cards.md#update-a-card); include `notify: true` to notify the people you add. A card table step is assigned on the step itself via [Update a step](card_table_steps.md#update-a-step) (`PUT /card_tables/steps/:id.json`), not the parent card.
* **Complete or reopen** — a to-do uses its [completion](todos.md#complete-a-to-do) endpoint (`POST`/`DELETE /todos/:id/completion.json`). A card table step uses [Change step completion status](card_table_steps.md#change-step-completion-status) — `PUT /card_tables/steps/:step_id/completions.json` with `completion: "on"` to complete or `"off"` to reopen. A card has no completion endpoint: it's completed by moving it into a done column and reopened by moving it out, via [Move a card](card_table_cards.md#move-a-card) (`POST /card_tables/cards/:id/moves.json` with the destination `column_id`).
* **Reschedule** — update a [to-do](todos.md#update-a-to-do) with `due_on` and, optionally, `starts_on`. A [card](card_table_cards.md#update-a-card) is rescheduled with `due_on` only — cards have no `starts_on` — and a card table [step](card_table_steps.md#update-a-step) likewise takes `due_on`, on its own update endpoint.

**Note:** these updates replace omitted fields. A to-do update and a card table step update both clear any field you don't send — including `assignee_ids`, `due_on`, and (for steps) `title` — so resend the current values you want to keep. A card update is the one that preserves omitted `title` and `content`, but even there `due_on` is cleared unless you resend it. In short: to change only assignees or only the due date, echo the record's other current fields in the same request.


Prioritize an assignment
------------------------

* `POST /my/priorities.json` adds a recording to "Up Next" — the current user's ordered list of prioritized assignments, returned as `priorities` in [Get assignments](#get-assignments). Returns `204 No Content`.

Identify the item by the **recording id** of the thing that carries the priority, not by the assignment id. [Get assignments](#get-assignments) normalizes a card table step under its parent card, so which id to send depends on what you're prioritizing:

* **A to-do, or a card itself** — send the item's top-level `id`.
* **A card table step that isn't prioritized yet** — send the step's own `id` from its parent card's `children`. Only already-prioritized top-level entries carry a `priority_recording_id`, so a step you haven't prioritized has just its own id.
* **A step that is already prioritized** — the top-level entry's `id` is the *card's*, so send that entry's `priority_recording_id`, which points at the prioritized step. Use it to reorder or deprioritize.

**Required parameters**: `id` — the recording id to prioritize.

###### Example JSON Request

```json
{
  "id": 1069479801
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"id":1069479801}' \
  https://3.basecampapi.com/$ACCOUNT_ID/my/priorities.json
```


Deprioritize an assignment
--------------------------

* `DELETE /my/priorities/1069479801.json` removes the recording with an ID of `1069479801` from Up Next. Returns `204 No Content`.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/my/priorities/1069479801.json
```


Reorder Up Next
---------------

* `POST /my/priority_moves.json` moves an already-prioritized recording to a new spot in Up Next. Returns `204 No Content`.

**Required parameters**:

* `source_id` — the recording id to move, chosen the same way as when [prioritizing](#prioritize-an-assignment).
* `position` — the 1-based position to move it to.

###### Example JSON Request

```json
{
  "source_id": 1069479801,
  "position": 1
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"source_id":1069479801,"position":1}' \
  https://3.basecampapi.com/$ACCOUNT_ID/my/priority_moves.json
```

Reordering validates `position` and, on failure, returns an error body of the form `{ "error": "..." }`:

* Missing `position` → `400 Bad Request`, `{ "error": "Position is required." }`.
* Non-integer `position` → `400 Bad Request`, `{ "error": "Position must be an integer." }`.
* `position` outside the list → `422 Unprocessable Entity`, `{ "error": "Position must be between 1 and N." }`, where `N` is the number of prioritized assignments.
* A recording that isn't prioritized → `422 Unprocessable Entity`, `{ "error": "Recording is not prioritized." }`.
* A recording you can't access → `404 Not Found`.
