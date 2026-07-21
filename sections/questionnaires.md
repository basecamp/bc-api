Questionnaires
==============

All automatic check-ins questions under a project are children of a questionnaire resource.

Endpoints:

- [Get questionnaire](#get-questionnaire)

Get questionnaire
-----------------

* `GET /questionnaires/2.json` will return the questionnaire with an ID of `2`.

To get the questionnaire ID for a project, see the [Get a Project][project] endpoint's `dock` payload. To retrieve its questions, see the [Get questions][questions] endpoint.

###### Example JSON Response
<!-- START GET /questionnaires/2.json -->
```json
{
  "id": 1069479839,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-28T17:23:17.508Z",
  "updated_at": "2026-05-28T17:23:29.596Z",
  "title": "Automatic Check-ins",
  "inherits_status": true,
  "type": "Questionnaire",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/questionnaires/1069479839.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/questionnaires/1069479839",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgzOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--805e1098ad25acde1b2378dfd3d8b7e59bb3cce8.json",
  "position": 6,
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
  "name": "Automatic Check-ins",
  "questions_count": 1,
  "questions_url": "https://3.basecampapi.com/195539477/questionnaires/1069479839/questions.json"
}
```
<!-- END GET /questionnaires/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/questionnaires/2.json
```


Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/questionnaires/2.json` → [Get questionnaire](#get-questionnaire)

[project]: projects.md#get-a-project
[questions]: questions.md#get-questions
