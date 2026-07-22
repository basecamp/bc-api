Questions
=========

Endpoints:

- [Get questions](#get-questions)
- [Get a question](#get-a-question)
- [Create a question](#create-a-question)
- [Update a question](#update-a-question)
- [Pause a question](#pause-a-question)
- [Resume a question](#resume-a-question)
- [Update notification settings](#update-notification-settings)
- [Trash a question][trash]

Get questions
-------------

* `GET /questionnaires/2/questions.json` will return a [paginated list][pagination] of questions in the questionnaire with ID of `2`.

###### Example JSON Response
<!-- START GET /questionnaires/2/questions.json -->
```json
[
  {
    "id": 1069479853,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-04-15T01:38:00.000Z",
    "updated_at": "2026-05-28T17:23:29.579Z",
    "title": "What did you work on today?",
    "inherits_status": true,
    "type": "Question",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/questions/1069479853.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/questions/1069479853",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg1Mz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--7564a2d1da596c874f0d6dba550c70472e64e932.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479853/subscription.json",
    "parent": {
      "id": 1069479839,
      "title": "Automatic Check-ins",
      "type": "Questionnaire",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/questionnaires/1069479839.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/questionnaires/1069479839"
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
      "updated_at": "2026-07-21T01:06:02.483Z",
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
    "paused": false,
    "schedule": {
      "frequency": "every_day",
      "days": [
        1,
        2,
        3,
        4,
        5
      ],
      "hour": 9,
      "minute": 0,
      "week_instance": null,
      "week_interval": null,
      "month_interval": null,
      "start_date": "2026-05-29",
      "duration": null,
      "end_date": null
    },
    "answers_count": 32,
    "answers_url": "https://3.basecampapi.com/195539477/questions/1069479853/answers.json"
  }
]
```
<!-- END GET /questionnaires/2/questions.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/questionnaires/2/questions.json
```

Get a question
--------------

* `GET /questions/2.json` will return the question with an ID of `2`.

###### Example JSON Response
<!-- START GET /questions/2.json -->
```json
{
  "id": 1069479853,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-04-15T01:38:00.000Z",
  "updated_at": "2026-05-28T17:23:29.579Z",
  "title": "What did you work on today?",
  "inherits_status": true,
  "type": "Question",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/questions/1069479853.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/questions/1069479853",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg1Mz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--7564a2d1da596c874f0d6dba550c70472e64e932.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479853/subscription.json",
  "parent": {
    "id": 1069479839,
    "title": "Automatic Check-ins",
    "type": "Questionnaire",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/questionnaires/1069479839.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/questionnaires/1069479839"
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
    "updated_at": "2026-07-21T01:06:02.483Z",
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
  "paused": false,
  "schedule": {
    "frequency": "every_day",
    "days": [
      1,
      2,
      3,
      4,
      5
    ],
    "hour": 9,
    "minute": 0,
    "week_instance": null,
    "week_interval": null,
    "month_interval": null,
    "start_date": "2026-05-29",
    "duration": null,
    "end_date": null
  },
  "answers_count": 32,
  "answers_url": "https://3.basecampapi.com/195539477/questions/1069479853/answers.json"
}
```
<!-- END GET /questions/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/questions/2.json
```


Create a question
-----------------

* `POST /questionnaires/2/questions.json` creates a question under the questionnaire with ID `2`.

**Required parameters**:
* `question[title]` - the question to ask.
* `question[schedule]` - a hash containing the schedule configuration:
  * `frequency` - one of `every_day`, `every_week`, `every_other_week`, `every_month`, or `on_certain_days`.
  * `time_of_day` - the time to ask, e.g. `"9:00am"`.
  * `days` - an array of day numbers (0=Sunday through 6=Saturday), e.g. `["1","2","3","4","5"]` for weekdays.

_Optional parameters_:

* `visible_to_clients` - a **top-level** boolean — a sibling of the `question` object, *not* inside it. When the project has clients enabled, whether the question is visible to them. Defaults to `false`; a **client** caller always creates client-visible records. See [Client visibility][client_visibility] to change it after creation.

This endpoint will return `201 Created` with the current JSON representation of the question if the creation was a success. See the [Get a question](#get-a-question) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "question": {
    "title": "What did you work on today?",
    "schedule": {
      "frequency": "every_day",
      "time_of_day": "5:00pm",
      "days": ["1", "2", "3", "4", "5"]
    }
  },
  "visible_to_clients": true
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"question":{"title":"What did you work on today?","schedule":{"frequency":"every_day","time_of_day":"5:00pm","days":["1","2","3","4","5"]}},"visible_to_clients":true}' \
  https://3.basecampapi.com/$ACCOUNT_ID/questionnaires/2/questions.json
```


Update a question
-----------------

* `PUT /questions/2.json` allows changing the question with an ID of `2`.

This endpoint will return `200 OK` with the current JSON representation of the question if the update was a success. See the [Get a question](#get-a-question) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "question": {
    "title": "What are you working on this week?",
    "schedule": {
      "frequency": "every_week",
      "time_of_day": "9:00am",
      "days": ["1"]
    }
  }
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"question":{"title":"What are you working on this week?","schedule":{"frequency":"every_week","time_of_day":"9:00am","days":["1"]}}}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/questions/2.json
```


Pause a question
----------------

* `POST /questions/2/pause.json` pauses the question with an ID of `2`.

Returns `200 OK` with `{"paused": true}`.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/questions/2/pause.json
```


Resume a question
-----------------

* `DELETE /questions/2/pause.json` resumes the question with an ID of `2`.

Returns `200 OK` with `{"paused": false}`.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/questions/2/pause.json
```


Update notification settings
----------------------------

* `PUT /questions/2/notification_settings.json` toggles notification settings for the question with an ID of `2`.

_Optional parameters_:

* `responding` - boolean, whether the authenticated user is responding to this question.
* `subscribed` - boolean, whether the authenticated user is subscribed to notifications for this question.

Returns `200 OK` with `{"responding": true/false, "subscribed": true/false}`.

###### Example JSON Request

```json
{
  "responding": true,
  "subscribed": false
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"responding":true,"subscribed":false}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/questions/2/notification_settings.json
```

Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/questionnaires/2/questions.json` → [Get questions](#get-questions)
* `GET /buckets/1/questions/2.json` → [Get a question](#get-a-question)
* `POST /buckets/1/questionnaires/2/questions.json` → [Create a question](#create-a-question)
* `PUT /buckets/1/questions/2.json` → [Update a question](#update-a-question)
* `POST /buckets/1/questions/2/pause.json` → [Pause a question](#pause-a-question)
* `DELETE /buckets/1/questions/2/pause.json` → [Resume a question](#resume-a-question)
* `PUT /buckets/1/questions/2/notification_settings.json` → [Update notification settings](#update-notification-settings)

[pagination]: ../README.md#pagination
[trash]: recordings.md#trash-a-recording
[client_visibility]: client_visibility.md
