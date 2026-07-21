Schedules
=========

All schedule entries under a project are children of a schedule resource.

Endpoints:

- [Get schedule](#get-schedule)
- [Update a schedule](#update-a-schedule)


Get schedule
------------

* `GET /schedules/2.json` will return the schedule with an ID of `2`.

To get the schedule ID for a project, see the [Get a project][1] endpoint's `dock` payload. To retrieve its schedule entries, see the [Get schedule entries][2] endpoint.

###### Example JSON Response
<!-- START GET /schedules/2.json -->
```json
{
  "id": 1069479831,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-28T17:23:17.372Z",
  "updated_at": "2026-05-28T17:29:04.984Z",
  "title": "Calendar",
  "inherits_status": true,
  "type": "Schedule",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/schedules/1069479831.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/schedules/1069479831",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgzMT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--302d13a0f9b5c82985735c0c42f03db1467440f1.json",
  "position": 4,
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
  "include_due_assignments": true,
  "entries_count": 1,
  "entries_url": "https://3.basecampapi.com/195539477/schedules/1069479831/entries.json"
}
```
<!-- END GET /schedules/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/schedules/2.json
```

Update a schedule
-----------------------

* `PUT /schedules/2.json` allows changing the schedule with an ID of `2`.

**Required parameters**:

* `include_due_assignments` - whether the schedule should include due dates from to-dos, cards and steps.

This endpoint will return `200 OK` with the current JSON representation of the schedule if the update was a success.

###### Example JSON Request

```json
{
  "schedule": {
    "include_due_assignments": false
  }
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"schedule": {"include_due_assignments": false}}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/schedules/2.json
```

Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/schedules/2.json` → [Get schedule](#get-schedule)
* `PUT /buckets/1/schedules/2.json` → [Update a schedule](#update-a-schedule)

[1]: projects.md#get-a-project
[2]: schedule_entries.md#get-schedule-entries
[3]: recordings.md#trash-a-recording
