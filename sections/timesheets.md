Timesheets
==========

Endpoints:

- [Get timesheet report](#get-timesheet-report)
- [Get timesheet for a project](#get-timesheet-for-a-project)
- [Get timesheet for a recording](#get-timesheet-for-a-recording)
- [Get a timesheet entry](#get-a-timesheet-entry)
- [Create a timesheet entry](#create-a-timesheet-entry)
- [Update a timesheet entry](#update-a-timesheet-entry)
- [Delete a timesheet entry](#delete-a-timesheet-entry)

Get timesheet report
--------------------

* `GET /reports/timesheet.json` will return a list of all timesheet entries across the account, within a given timeframe.

**Note:** This endpoint is currently not paginated.

_Optional query parameters_:

This endpoint without any parameters returns only timesheet entries for the last month. 

* `start_date` - report start date (ISO 8601). If provided also the end_date is
    required.
* `end_date` - report end date (ISO 8601). If provided also the start_date is
    required.
* `person_id` - single [person][1] ID. Default: Everyone.
* `bucket_id` - single [project][2] ID. Default: All projects.

###### Example JSON Response
<!-- START GET /reports/timesheet.json -->
```json
[
  {
    "id": 1069480283,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-05-28T17:29:05.460Z",
    "updated_at": "2026-05-28T17:29:05.460Z",
    "title": "Timesheet entry",
    "inherits_status": true,
    "type": "Timesheet::Entry",
    "url": "https://3.basecampapi.com/195539477/projects/2085958505/timesheet/entries/1069480283.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958505/timesheet/entries/1069480283",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI4Mz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--8c8ab3f872a17547f4b5ad4414d7ee423790d8bc.json",
    "parent": {
      "id": 1069479842,
      "title": "We won Leto!",
      "type": "Message",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/messages/1069479842.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069479842"
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
    "date": "2026-07-19",
    "description": "Team Meeting Prep",
    "hours": "2.0",
    "person": {
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
  }
]
```
<!-- END GET /reports/timesheet.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/reports/timesheet.json
```

Get timesheet for a project
---------------------------

* `GET /projects/1/timesheet.json` will return a [paginated list][pagination] of timesheet entries in the project with an ID of `1`.

This includes all entries across the project: entries logged directly to the project as well as entries logged on specific to-dos, messages, cards, and other recordings. Each entry's `parent` field shows which recording it belongs to. For entries logged at the project level, the parent type is `Timesheet`.

###### Example JSON Response
<!-- START GET /projects/1/timesheet.json -->
```json
[
  {
    "id": 1069480283,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-05-28T17:29:05.460Z",
    "updated_at": "2026-05-28T17:29:05.460Z",
    "title": "Timesheet entry",
    "inherits_status": true,
    "type": "Timesheet::Entry",
    "url": "https://3.basecampapi.com/195539477/projects/2085958505/timesheet/entries/1069480283.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958505/timesheet/entries/1069480283",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI4Mz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--8c8ab3f872a17547f4b5ad4414d7ee423790d8bc.json",
    "parent": {
      "id": 1069479842,
      "title": "We won Leto!",
      "type": "Message",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/messages/1069479842.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069479842"
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
    "date": "2026-07-19",
    "description": "Team Meeting Prep",
    "hours": "2.0",
    "person": {
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
  }
]
```
<!-- END GET /projects/1/timesheet.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/projects/1/timesheet.json
```

Get timesheet for a recording
-----------------------------

* `GET /recordings/2/timesheet.json` will return a [paginated list][pagination] of timesheet entries for the recording with ID of `2`.

###### Example JSON Response
<!-- START GET /recordings/2/timesheet.json -->
```json
[
  {
    "id": 1069480283,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-05-28T17:29:05.460Z",
    "updated_at": "2026-05-28T17:29:05.460Z",
    "title": "Timesheet entry",
    "inherits_status": true,
    "type": "Timesheet::Entry",
    "url": "https://3.basecampapi.com/195539477/projects/2085958505/timesheet/entries/1069480283.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958505/timesheet/entries/1069480283",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI4Mz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--8c8ab3f872a17547f4b5ad4414d7ee423790d8bc.json",
    "parent": {
      "id": 1069479842,
      "title": "We won Leto!",
      "type": "Message",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/messages/1069479842.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069479842"
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
    "date": "2026-07-19",
    "description": "Team Meeting Prep",
    "hours": "2.0",
    "person": {
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
  }
]
```
<!-- END GET /recordings/2/timesheet.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/timesheet.json
```

Get a timesheet entry
---------------------

* `GET /timesheet_entries/2.json` will return the timesheet entry with an ID of `2`.

###### Example JSON Response
<!-- START GET /timesheet_entries/2.json -->
```json
{
  "id": 1069480408,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-07-21T01:05:32.813Z",
  "updated_at": "2026-07-21T01:05:32.813Z",
  "title": "Timesheet entry",
  "inherits_status": true,
  "type": "Timesheet::Entry",
  "url": "https://3.basecampapi.com/195539477/projects/2085958505/timesheet/entries/1069480408.json",
  "app_url": "https://3.basecamp.com/195539477/projects/2085958505/timesheet/entries/1069480408",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDQwOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--366248576000fe08b23f79367f1553672929853e.json",
  "parent": {
    "id": 1069479842,
    "title": "We won Leto!",
    "type": "Message",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/messages/1069479842.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069479842"
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
  "date": "2026-07-20",
  "description": "API docs example",
  "hours": "1.5",
  "person": {
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
}
```
<!-- END GET /timesheet_entries/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/timesheet_entries/2.json
```

Create a timesheet entry
------------------------

* `POST /recordings/2/timesheet/entries.json` creates a timesheet entry under the recording with ID `2`.

The recording can be any timesheetable type: a message, to-do, card, document, upload, schedule entry, or the project timesheet itself.

**Project-level entries**: Time can be logged directly to a project without associating it with a specific to-do or message. To do this, use the project's timesheet recording ID in the URL above. Unlike other tools, the timesheet doesn't appear in the project's `dock` array — instead, check the project's `timesheet_enabled` flag. When it's `true`, you can access the project timesheet at `GET /projects/1/timesheet.json`. The entries in that response include a `parent` field; for project-level entries, the parent type is `Timesheet` and its `id` is the recording ID to use in the create URL.

**Required parameters**:

* `date` - the date the time was spent (ISO 8601, e.g. `2024-05-16`).
* `hours` - the number of hours. Accepts decimal (`1.5`) or time format (`1:30`).

_Optional parameters_:

* `description` - a note about the work performed.
* `person_id` - the [person][1] the time is for. Defaults to the authenticated user. Must be a non-client member of the project.

This endpoint will return `201 Created` with the current JSON representation of the timesheet entry if the creation was a success. See the [Get timesheet for a project](#get-timesheet-for-a-project) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "date": "2024-05-16",
  "hours": "1:30",
  "description": "Client meeting prep"
}
```

###### Example JSON Response
<!-- START POST /recordings/2/timesheet/entries.json -->
```json
{
  "id": 1069480408,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-07-21T01:05:32.813Z",
  "updated_at": "2026-07-21T01:05:32.813Z",
  "title": "Timesheet entry",
  "inherits_status": true,
  "type": "Timesheet::Entry",
  "url": "https://3.basecampapi.com/195539477/projects/2085958505/timesheet/entries/1069480408.json",
  "app_url": "https://3.basecamp.com/195539477/projects/2085958505/timesheet/entries/1069480408",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDQwOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--366248576000fe08b23f79367f1553672929853e.json",
  "parent": {
    "id": 1069479842,
    "title": "We won Leto!",
    "type": "Message",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/messages/1069479842.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069479842"
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
  "date": "2026-07-20",
  "description": "API docs example",
  "hours": "1.5",
  "person": {
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
}
```
<!-- END POST /recordings/2/timesheet/entries.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"date":"2024-05-16","hours":"1:30","description":"Client meeting prep"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/timesheet/entries.json
```

Update a timesheet entry
------------------------

* `PUT /timesheet_entries/2.json` allows changing the timesheet entry with an ID of `2`.

This endpoint will return `200 OK` with the current JSON representation of the timesheet entry if the update was a success. See the [Get timesheet for a project](#get-timesheet-for-a-project) endpoint for more info on the payload.

_Optional parameters_: Only pass the parameters you want to change.

* `date` - the date the time was spent (ISO 8601).
* `hours` - the number of hours. Accepts decimal (`1.5`) or time format (`1:30`).
* `description` - a note about the work performed.
* `person_id` - the [person][1] the time is for. Must be a non-client member of the project.

###### Example JSON Request

```json
{
  "hours": "2.5",
  "description": "Updated description"
}
```

###### Example JSON Response
<!-- START PUT /timesheet_entries/2.json -->
```json
{
  "id": 1069480408,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-07-21T01:05:32.813Z",
  "updated_at": "2026-07-21T01:05:33.782Z",
  "title": "Timesheet entry",
  "inherits_status": true,
  "type": "Timesheet::Entry",
  "url": "https://3.basecampapi.com/195539477/projects/2085958505/timesheet/entries/1069480408.json",
  "app_url": "https://3.basecamp.com/195539477/projects/2085958505/timesheet/entries/1069480408",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDQwOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--366248576000fe08b23f79367f1553672929853e.json",
  "parent": {
    "id": 1069479842,
    "title": "We won Leto!",
    "type": "Message",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/messages/1069479842.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069479842"
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
  "date": "2026-07-20",
  "description": "Updated via API",
  "hours": "2.5",
  "person": {
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
}
```
<!-- END PUT /timesheet_entries/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -X PUT -d '{"hours":"2.5","description":"Updated description"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/timesheet_entries/2.json
```

Delete a timesheet entry
------------------------

* `DELETE /timesheet_entries/2.json` will delete the timesheet entry with an ID of `2`.

This endpoint will return `204 No Content` if the delete was successful. No parameters are required.

The entry is permanently deleted and cannot be recovered.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/timesheet_entries/2.json
```

Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /projects/1/timesheet.json` → [Get timesheet for a project](#get-timesheet-for-a-project)
* `GET /projects/1/recordings/2/timesheet.json` → [Get timesheet for a recording](#get-timesheet-for-a-recording)
* `POST /projects/1/recordings/2/timesheet/entries.json` → [Create a timesheet entry](#create-a-timesheet-entry)

[1]: people.md#people
[2]: projects.md#projects
