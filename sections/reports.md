Reports
=======

Endpoints:

- [Get to-do assignments](#get-to-do-assignments)
- [Get to-do assignments for a person](#get-to-do-assignments-for-a-person)
- [Get overdue to-dos](#get-overdue-to-dos)
- [Get upcoming schedule](#get-upcoming-schedule)

Get to-do assignments
---------------------

* `GET /reports/todos/assigned.json` will return a list of all people who can have to-dos assigned to them.

This endpoint is useful for building a list of people to then retrieve their individual to-do assignments.

###### Example JSON Response
<!-- START GET /reports/todos/assigned.json -->
```json
[
  {
    "id": 1049715915,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--56bb1f99675fd8fe08f93a706a5d2ddaa8412625",
    "name": "Amy Rivera",
    "personable_type": "User",
    "title": "Central Web Coordinator",
    "tagline": "I never said most of the things I said",
    "location": null,
    "created_at": "2026-05-28T17:22:23.206Z",
    "updated_at": "2026-05-28T17:22:23.206Z",
    "email_address": "amy@honchodesign.com",
    "bio": "I never said most of the things I said",
    "admin": false,
    "owner": false,
    "client": false,
    "employee": false,
    "time_zone": "America/Chicago",
    "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMtkkT4=--9927c47a4cbee30a7f9aea667882496aba799149/avatar",
    "can_ping": true,
    "can_manage_projects": true,
    "can_manage_people": true,
    "can_access_timesheet": true,
    "can_access_hill_charts": true
  }
]
```
<!-- END GET /reports/todos/assigned.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/reports/todos/assigned.json
```

Get to-do assignments for a person
----------------------------------

* `GET /reports/todos/assigned/1.json` will return a list of all active, pending to-dos assigned to the person with an ID of `1`.

_Optional query parameters_:

* `group_by` - when set to `bucket`, will group to-dos by project. When set to `date`, will group by due date. Default: `bucket`.

###### Example JSON Response
<!-- START GET /reports/todos/assigned/1.json -->
```json
{
  "person": {
    "id": 1049715915,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--56bb1f99675fd8fe08f93a706a5d2ddaa8412625",
    "name": "Amy Rivera",
    "personable_type": "User",
    "title": "Central Web Coordinator",
    "tagline": "I never said most of the things I said",
    "location": null,
    "created_at": "2026-05-28T17:22:23.206Z",
    "updated_at": "2026-05-28T17:22:23.206Z",
    "email_address": "amy@honchodesign.com",
    "bio": "I never said most of the things I said",
    "admin": false,
    "owner": false,
    "client": false,
    "employee": false,
    "time_zone": "America/Chicago",
    "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMtkkT4=--9927c47a4cbee30a7f9aea667882496aba799149/avatar",
    "can_ping": true,
    "can_manage_projects": true,
    "can_manage_people": true,
    "can_access_timesheet": true,
    "can_access_hill_charts": true
  },
  "grouped_by": "bucket",
  "todos": [
    {
      "id": 1069479538,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-04-28T23:00:00.000Z",
      "updated_at": "2026-04-28T23:00:00.000Z",
      "title": "Amy vs. Sharon",
      "inherits_status": true,
      "type": "Todo",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958502/todos/1069479538.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/todos/1069479538",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTUzOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--8deb126e1f217488d3471712aadb05e8aa62aecf.json",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479538/subscription.json",
      "comments_count": 0,
      "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479538/comments.json",
      "boosts_count": 0,
      "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479538/boosts.json",
      "position": 2,
      "parent": {
        "id": 1069479536,
        "title": "Group D",
        "type": "Todolist",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958502/todolists/1069479536.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/todolists/1069479536"
      },
      "bucket": {
        "id": 2085958502,
        "name": "Honcho Design Newsroom",
        "type": "Project"
      },
      "creator": {
        "id": 1049715918,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--d6212bd7e60bf63ea61797589b2638cbbf2d4ed7",
        "name": "Brian Jenks",
        "personable_type": "User",
        "title": "International Branding Liason",
        "tagline": null,
        "location": null,
        "created_at": "2026-05-28T17:22:24.207Z",
        "updated_at": "2026-05-28T17:22:24.207Z",
        "email_address": "brian@honchodesign.com",
        "bio": null,
        "admin": false,
        "owner": false,
        "client": false,
        "employee": false,
        "time_zone": "America/Chicago",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBM5kkT4=--50075f17f313c1198fb6f27e5d466327804dfd22/avatar",
        "can_ping": true,
        "can_manage_projects": true,
        "can_manage_people": true,
        "can_access_timesheet": true,
        "can_access_hill_charts": true
      },
      "description": "",
      "description_attachments": [],
      "completed": false,
      "content": "Amy vs. Sharon",
      "starts_on": null,
      "due_on": null,
      "assignees": [
        {
          "id": 1049715915,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--56bb1f99675fd8fe08f93a706a5d2ddaa8412625",
          "name": "Amy Rivera",
          "personable_type": "User",
          "title": "Central Web Coordinator",
          "tagline": "I never said most of the things I said",
          "location": null,
          "created_at": "2026-05-28T17:22:23.206Z",
          "updated_at": "2026-05-28T17:22:23.206Z",
          "email_address": "amy@honchodesign.com",
          "bio": "I never said most of the things I said",
          "admin": false,
          "owner": false,
          "client": false,
          "employee": false,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMtkkT4=--9927c47a4cbee30a7f9aea667882496aba799149/avatar",
          "can_ping": true,
          "can_manage_projects": true,
          "can_manage_people": true,
          "can_access_timesheet": true,
          "can_access_hill_charts": true
        }
      ],
      "completion_subscribers": [],
      "completion_url": "https://3.basecampapi.com/195539477/todos/1069479538/completion.json",
      "steps": []
    }
  ]
}
```
<!-- END GET /reports/todos/assigned/1.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/reports/todos/assigned/1.json
```

Get overdue to-dos
------------------

* `GET /reports/todos/overdue.json` will return all overdue to-dos across all projects, grouped by how late they are.

The response includes four groups:
* `under_a_week_late` - to-dos due within the last 7 days
* `over_a_week_late` - to-dos due between 7 and 30 days ago
* `over_a_month_late` - to-dos due between 30 and 90 days ago
* `over_three_months_late` - to-dos due more than 90 days ago

###### Example JSON Response
<!-- START GET /reports/todos/overdue.json -->
```json
{
  "under_a_week_late": [],
  "over_a_week_late": [],
  "over_a_month_late": [
    {
      "id": 1069479805,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-05-21T23:39:00.000Z",
      "updated_at": "2026-05-28T17:23:17.199Z",
      "title": "Check campaign results",
      "inherits_status": true,
      "type": "Todo",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todos/1069479805.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todos/1069479805",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgwNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--7be2fe2eb73c2a3174f549140c061f808ad54907.json",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479805/subscription.json",
      "comments_count": 0,
      "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479805/comments.json",
      "boosts_count": 0,
      "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479805/boosts.json",
      "position": 4,
      "parent": {
        "id": 1069479800,
        "title": "TV Ad",
        "type": "Todolist",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todolists/1069479800.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todolists/1069479800"
      },
      "bucket": {
        "id": 2085958504,
        "name": "Honcho HQ",
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
      "content": "Check campaign results",
      "starts_on": null,
      "due_on": "2026-06-20",
      "repetition_schedule": {
        "frequency": "every_day",
        "days": [],
        "hour": 0,
        "minute": 0,
        "week_instance": null,
        "week_interval": null,
        "month_interval": null,
        "start_date": "2026-06-20",
        "duration": null,
        "end_date": null
      },
      "assignees": [],
      "completion_subscribers": [],
      "completion_url": "https://3.basecampapi.com/195539477/todos/1069479805/completion.json",
      "steps": []
    },
    {
      "id": 1069479803,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-05-21T23:29:00.000Z",
      "updated_at": "2026-05-21T23:29:00.000Z",
      "title": "Check initial campaign results",
      "inherits_status": true,
      "type": "Todo",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todos/1069479803.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todos/1069479803",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgwMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--d15f463f4a2042c5c3901d0dd46eeb66ffacc943.json",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479803/subscription.json",
      "comments_count": 0,
      "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479803/comments.json",
      "boosts_count": 0,
      "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479803/boosts.json",
      "position": 2,
      "parent": {
        "id": 1069479800,
        "title": "TV Ad",
        "type": "Todolist",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todolists/1069479800.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todolists/1069479800"
      },
      "bucket": {
        "id": 2085958504,
        "name": "Honcho HQ",
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
      "content": "Check initial campaign results",
      "starts_on": null,
      "due_on": "2026-06-19",
      "assignees": [],
      "completion_subscribers": [],
      "completion_url": "https://3.basecampapi.com/195539477/todos/1069479803/completion.json",
      "steps": []
    },
    {
      "id": 1069479804,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-05-21T23:38:00.000Z",
      "updated_at": "2026-05-21T23:38:00.000Z",
      "title": "Render all Ad variants",
      "inherits_status": true,
      "type": "Todo",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todos/1069479804.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todos/1069479804",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgwND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--798eff739fee1807fbfe27cfa14c54c10ab99609.json",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479804/subscription.json",
      "comments_count": 0,
      "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479804/comments.json",
      "boosts_count": 0,
      "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479804/boosts.json",
      "position": 3,
      "parent": {
        "id": 1069479800,
        "title": "TV Ad",
        "type": "Todolist",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todolists/1069479800.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todolists/1069479800"
      },
      "bucket": {
        "id": 2085958504,
        "name": "Honcho HQ",
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
      "content": "Render all Ad variants",
      "starts_on": "2026-06-11",
      "due_on": "2026-06-18",
      "assignees": [
        {
          "id": 1049715938,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--4ccc567a0a3b10e354bca909b704637b601f0b16",
          "name": "Annie Bryan",
          "personable_type": "User",
          "title": "Central Markets Manager",
          "tagline": "To open a store is easy, to keep it open is an art",
          "location": null,
          "created_at": "2026-05-28T17:22:29.167Z",
          "updated_at": "2026-05-28T17:22:29.167Z",
          "email_address": "annie@honchodesign.com",
          "bio": "To open a store is easy, to keep it open is an art",
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOJkkT4=--732a71fbd28ec10d9bf4466abd3588a8bea40bdb/avatar",
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
        {
          "id": 1049715939,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--91bd4d39e2f4af1d814a0b480e809d15a51df239",
          "name": "Cheryl Walters",
          "personable_type": "User",
          "title": "Corporate Integration Director",
          "tagline": "A joke is a very serious thing",
          "location": null,
          "created_at": "2026-05-28T17:22:29.505Z",
          "updated_at": "2026-05-28T17:22:29.505Z",
          "email_address": "cheryl@honchodesign.com",
          "bio": "A joke is a very serious thing",
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBONkkT4=--b57b5a44335d4c3ba1a2585abd6e5c7e4c85fdd6/avatar",
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
        {
          "id": 1049715940,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk0MD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--8a036dc6e0dee6b7db74851189b981fe69f4172d",
          "name": "Jared Davis",
          "personable_type": "User",
          "title": "International Tactics Facilitator",
          "tagline": "Oh, so they have internet on computers now!",
          "location": null,
          "created_at": "2026-05-28T17:22:29.827Z",
          "updated_at": "2026-05-28T17:22:29.827Z",
          "email_address": "jared@honchodesign.com",
          "bio": "Oh, so they have internet on computers now!",
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBORkkT4=--2667d9ced3ec021946197cbb6c3083f0f95f3b6a/avatar",
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
        {
          "id": 1049715941,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk0MT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--eaa5611b844193684f168e562045ddad5b56e397",
          "name": "Jennifer Hemmersmith Young",
          "personable_type": "User",
          "title": "Lead Configuration Manager",
          "tagline": null,
          "location": null,
          "created_at": "2026-05-28T17:22:30.128Z",
          "updated_at": "2026-05-28T17:22:30.128Z",
          "email_address": "jennifer@honchodesign.com",
          "bio": null,
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOVkkT4=--33e3fc268c87411378691c71b6f13658e0b40967/avatar",
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
        {
          "id": 1049715942,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--9e2080944c2f4ef95314dc6118f33af5972932a1",
          "name": "Josh Fiske",
          "personable_type": "User",
          "title": "Future Paradigm Planner",
          "tagline": null,
          "location": null,
          "created_at": "2026-05-28T17:22:30.459Z",
          "updated_at": "2026-05-28T17:22:30.459Z",
          "email_address": "josh@honchodesign.com",
          "bio": null,
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOZkkT4=--b8553b154990a1112ab6275b749296c4a3b56334/avatar",
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
        {
          "id": 1049715943,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk0Mz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--b0c6d5901972863f2e810d0076490e014fe01bdd",
          "name": "Nicole Katz",
          "personable_type": "User",
          "title": "Legacy Usability Planner",
          "tagline": null,
          "location": null,
          "created_at": "2026-05-28T17:22:30.773Z",
          "updated_at": "2026-05-28T17:22:30.773Z",
          "email_address": "nicole@honchodesign.com",
          "bio": null,
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOdkkT4=--1d2b80e583133f93afe008f88166b674fc0287a4/avatar",
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
        {
          "id": 1049715944,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk0ND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--5c49e7f857f7a2aea319ae399f8b00eb63123ef9",
          "name": "Steve Marsh",
          "personable_type": "User",
          "title": "Legacy Directives Strategist",
          "tagline": "You can do it!",
          "location": null,
          "created_at": "2026-05-28T17:22:31.108Z",
          "updated_at": "2026-05-28T17:22:31.108Z",
          "email_address": "steve@honchodesign.com",
          "bio": "You can do it!",
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOhkkT4=--b169e35b345bcc26eca6964b7ef7de2c16b6f238/avatar",
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
        {
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
        }
      ],
      "completion_subscribers": [],
      "completion_url": "https://3.basecampapi.com/195539477/todos/1069479804/completion.json",
      "steps": []
    },
    {
      "id": 1069479861,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-04-15T06:26:00.000Z",
      "updated_at": "2026-04-15T06:26:00.000Z",
      "title": "Make to-do lists",
      "inherits_status": true,
      "type": "Todo",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todos/1069479861.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todos/1069479861",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg2MT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--898d09d82b41453441a5f04a6c7550c439cdaeeb.json",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479861/subscription.json",
      "comments_count": 0,
      "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479861/comments.json",
      "boosts_count": 0,
      "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479861/boosts.json",
      "position": 2,
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
        "id": 1049715930,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzMD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--322099b137f9e0b6bc944b5b9fe7a2692da94814",
        "name": "Sharon Bradford",
        "personable_type": "User",
        "title": "Principal Branding Administrator",
        "tagline": null,
        "location": null,
        "created_at": "2026-05-28T17:22:28.137Z",
        "updated_at": "2026-05-28T17:22:28.137Z",
        "email_address": "sharon@honchodesign.com",
        "bio": null,
        "admin": false,
        "owner": false,
        "client": false,
        "employee": false,
        "time_zone": "America/Chicago",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNpkkT4=--789594e5e542ab99e467a51c9dec0a9035abc0e0/avatar",
        "can_ping": true,
        "can_manage_projects": true,
        "can_manage_people": true,
        "can_access_timesheet": true,
        "can_access_hill_charts": true
      },
      "description": "",
      "description_attachments": [],
      "completed": false,
      "content": "Make to-do lists",
      "starts_on": null,
      "due_on": "2026-05-29",
      "assignees": [
        {
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
        }
      ],
      "completion_subscribers": [],
      "completion_url": "https://3.basecampapi.com/195539477/todos/1069479861/completion.json",
      "steps": []
    },
    {
      "id": 1069479801,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-05-21T22:36:00.000Z",
      "updated_at": "2026-05-21T22:36:00.000Z",
      "title": "Why isn't this done yet?",
      "inherits_status": true,
      "type": "Todo",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todos/1069479801.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todos/1069479801",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgwMT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--d7ef250095e7127009bd730d5d13ba76b7f8038b.json",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479801/subscription.json",
      "comments_count": 0,
      "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479801/comments.json",
      "boosts_count": 0,
      "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479801/boosts.json",
      "position": 1,
      "parent": {
        "id": 1069479800,
        "title": "TV Ad",
        "type": "Todolist",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todolists/1069479800.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todolists/1069479800"
      },
      "bucket": {
        "id": 2085958504,
        "name": "Honcho HQ",
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
      "content": "Why isn't this done yet?",
      "starts_on": null,
      "due_on": "2026-05-25",
      "assignees": [
        {
          "id": 1049715938,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--4ccc567a0a3b10e354bca909b704637b601f0b16",
          "name": "Annie Bryan",
          "personable_type": "User",
          "title": "Central Markets Manager",
          "tagline": "To open a store is easy, to keep it open is an art",
          "location": null,
          "created_at": "2026-05-28T17:22:29.167Z",
          "updated_at": "2026-05-28T17:22:29.167Z",
          "email_address": "annie@honchodesign.com",
          "bio": "To open a store is easy, to keep it open is an art",
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOJkkT4=--732a71fbd28ec10d9bf4466abd3588a8bea40bdb/avatar",
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
        {
          "id": 1049715939,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--91bd4d39e2f4af1d814a0b480e809d15a51df239",
          "name": "Cheryl Walters",
          "personable_type": "User",
          "title": "Corporate Integration Director",
          "tagline": "A joke is a very serious thing",
          "location": null,
          "created_at": "2026-05-28T17:22:29.505Z",
          "updated_at": "2026-05-28T17:22:29.505Z",
          "email_address": "cheryl@honchodesign.com",
          "bio": "A joke is a very serious thing",
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBONkkT4=--b57b5a44335d4c3ba1a2585abd6e5c7e4c85fdd6/avatar",
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
        {
          "id": 1049715940,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk0MD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--8a036dc6e0dee6b7db74851189b981fe69f4172d",
          "name": "Jared Davis",
          "personable_type": "User",
          "title": "International Tactics Facilitator",
          "tagline": "Oh, so they have internet on computers now!",
          "location": null,
          "created_at": "2026-05-28T17:22:29.827Z",
          "updated_at": "2026-05-28T17:22:29.827Z",
          "email_address": "jared@honchodesign.com",
          "bio": "Oh, so they have internet on computers now!",
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBORkkT4=--2667d9ced3ec021946197cbb6c3083f0f95f3b6a/avatar",
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
        {
          "id": 1049715941,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk0MT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--eaa5611b844193684f168e562045ddad5b56e397",
          "name": "Jennifer Hemmersmith Young",
          "personable_type": "User",
          "title": "Lead Configuration Manager",
          "tagline": null,
          "location": null,
          "created_at": "2026-05-28T17:22:30.128Z",
          "updated_at": "2026-05-28T17:22:30.128Z",
          "email_address": "jennifer@honchodesign.com",
          "bio": null,
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOVkkT4=--33e3fc268c87411378691c71b6f13658e0b40967/avatar",
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
        {
          "id": 1049715942,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--9e2080944c2f4ef95314dc6118f33af5972932a1",
          "name": "Josh Fiske",
          "personable_type": "User",
          "title": "Future Paradigm Planner",
          "tagline": null,
          "location": null,
          "created_at": "2026-05-28T17:22:30.459Z",
          "updated_at": "2026-05-28T17:22:30.459Z",
          "email_address": "josh@honchodesign.com",
          "bio": null,
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOZkkT4=--b8553b154990a1112ab6275b749296c4a3b56334/avatar",
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
        {
          "id": 1049715943,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk0Mz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--b0c6d5901972863f2e810d0076490e014fe01bdd",
          "name": "Nicole Katz",
          "personable_type": "User",
          "title": "Legacy Usability Planner",
          "tagline": null,
          "location": null,
          "created_at": "2026-05-28T17:22:30.773Z",
          "updated_at": "2026-05-28T17:22:30.773Z",
          "email_address": "nicole@honchodesign.com",
          "bio": null,
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOdkkT4=--1d2b80e583133f93afe008f88166b674fc0287a4/avatar",
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
        {
          "id": 1049715944,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk0ND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--5c49e7f857f7a2aea319ae399f8b00eb63123ef9",
          "name": "Steve Marsh",
          "personable_type": "User",
          "title": "Legacy Directives Strategist",
          "tagline": "You can do it!",
          "location": null,
          "created_at": "2026-05-28T17:22:31.108Z",
          "updated_at": "2026-05-28T17:22:31.108Z",
          "email_address": "steve@honchodesign.com",
          "bio": "You can do it!",
          "admin": false,
          "owner": false,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOhkkT4=--b169e35b345bcc26eca6964b7ef7de2c16b6f238/avatar",
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
        {
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
        }
      ],
      "completion_subscribers": [],
      "completion_url": "https://3.basecampapi.com/195539477/todos/1069479801/completion.json",
      "steps": []
    }
  ],
  "over_three_months_late": []
}
```
<!-- END GET /reports/todos/overdue.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/reports/todos/overdue.json
```

Get upcoming schedule
---------------------

* `GET /reports/schedules/upcoming.json` will return schedule entries and assignable items within a specified date window. This endpoint is preserved as the canonical API path; the BC5 `/calendar` web view is HTML-only.

**Required query parameters**:

* `window_starts_on` - the start date of the window (ISO 8601, `YYYY-MM-DD`)
* `window_ends_on` - the end date of the window (ISO 8601, `YYYY-MM-DD`)

The response includes:
* `schedule_entries` - one-time schedule entries within the window
* `recurring_schedule_entry_occurrences` - occurrences of recurring schedule entries within the window
* `assignables` - to-dos, cards, and steps with due dates within the window

###### Example JSON Response
<!-- START GET /reports/schedules/upcoming.json -->
```json
{
  "schedule_entries": [
    {
      "id": 1069479796,
      "status": "active",
      "visible_to_clients": false,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/schedule_entries/1069479796.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/schedule_entries/1069479796",
      "type": "ScheduleEntry",
      "summary": "Amy's Sabbatical",
      "all_day": true,
      "recurring": false,
      "starts_at": "2026-06-18",
      "ends_at": "2026-07-30",
      "creator": {
        "id": 1049715913,
        "name": "Victor Cooper",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
      },
      "participants": [],
      "bucket": {
        "id": 2085958504,
        "name": "Honcho HQ"
      },
      "comments_count": 0
    },
    {
      "id": 1069480280,
      "status": "active",
      "visible_to_clients": false,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/schedule_entries/1069480280.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/schedule_entries/1069480280",
      "type": "ScheduleEntry",
      "summary": "Team Meeting",
      "all_day": false,
      "recurring": false,
      "starts_at": "2026-07-21T06:05:47.135Z",
      "ends_at": "2026-07-21T10:05:47.135Z",
      "creator": {
        "id": 1049715913,
        "name": "Victor Cooper",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
      },
      "participants": [
        {
          "id": 1049715944,
          "name": "Steve Marsh",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOhkkT4=--b169e35b345bcc26eca6964b7ef7de2c16b6f238/avatar"
        }
      ],
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop"
      },
      "comments_count": 0
    }
  ],
  "recurring_schedule_entry_occurrences": [
    {
      "id": 1069479787,
      "status": "active",
      "visible_to_clients": false,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/schedule_entries/1069479787/occurrences/20260722.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/schedule_entries/1069479787/occurrences/20260722",
      "type": "ScheduleEntry",
      "summary": "Taco Tuesday",
      "all_day": true,
      "recurring": true,
      "starts_at": "2026-07-22",
      "ends_at": "2026-07-22",
      "creator": {
        "id": 1049715913,
        "name": "Victor Cooper",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
      },
      "participants": [
        {
          "id": 1049715913,
          "name": "Victor Cooper",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
        },
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
        }
      ],
      "bucket": {
        "id": 2085958504,
        "name": "Honcho HQ"
      },
      "comments_count": 0
    },
    {
      "id": 1069479786,
      "status": "active",
      "visible_to_clients": false,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/schedule_entries/1069479786/occurrences/20260726.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/schedule_entries/1069479786/occurrences/20260726",
      "type": "ScheduleEntry",
      "summary": "Weekly Team Meeting",
      "all_day": false,
      "recurring": true,
      "starts_at": "2026-07-26T00:00:00.000-05:00",
      "ends_at": "2026-07-25T13:00:00.000-05:00",
      "creator": {
        "id": 1049715913,
        "name": "Victor Cooper",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
      },
      "participants": [],
      "bucket": {
        "id": 2085958504,
        "name": "Honcho HQ"
      },
      "comments_count": 0
    }
  ],
  "assignables": []
}
```
<!-- END GET /reports/schedules/upcoming.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" "https://3.basecampapi.com/$ACCOUNT_ID/reports/schedules/upcoming.json?window_starts_on=2025-10-10&window_ends_on=2025-10-17"
```

[pagination]: ../README.md#pagination
[people]: people.md#people
[projects]: projects.md#projects
