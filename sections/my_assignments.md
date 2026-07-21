My assignments
===============

Endpoints for retrieving the current user's assignments, including active assignments split by priority, completed assignments, and due assignments filtered by time scope.

Each assignment includes its content, type, bucket, parent, assignees, due dates, completion status, and any child assignments (e.g. card steps nested under their parent card).

**Note:** These endpoints return the full result set and are not paginated.

Endpoints:

- [Get assignments](#get-assignments)
- [Get completed assignments](#get-completed-assignments)
- [Get due assignments](#get-due-assignments)


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
