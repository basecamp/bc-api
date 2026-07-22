Schedule entries
================

Endpoints:

- [Get schedule entries](#get-schedule-entries)
- [Get a schedule entry](#get-a-schedule-entry)
- [Create a schedule entry](#create-a-schedule-entry)
- [Update a schedule entry](#update-a-schedule-entry)
- [Trash a schedule entry][trash]

Get schedule entries
--------------------

* `GET /schedules/3/entries.json` will return a [paginated list][pagination] of active schedule entries in the schedule with ID of `3`.

To get the schedule ID for a project, see the [Get schedule][schedule] endpoint.

_Optional query parameters_:

* `status` - when set to `archived` or `trashed`, will return archived or trashed schedule entries that are in this schedule.

###### Example JSON Response
<!-- START GET /schedules/3/entries.json -->
```json
[
  {
    "id": 1069480280,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-05-28T17:29:04.741Z",
    "updated_at": "2026-05-28T17:29:04.965Z",
    "title": "Team Meeting",
    "inherits_status": true,
    "type": "Schedule::Entry",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/schedule_entries/1069480280.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/schedule_entries/1069480280",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI4MD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--da128107535b57443e391ebc9ce03a6d5c2097a8.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480280/subscription.json",
    "comments_count": 0,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480280/comments.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480280/boosts.json",
    "parent": {
      "id": 1069479831,
      "title": "Calendar",
      "type": "Schedule",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/schedules/1069479831.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/schedules/1069479831"
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
    "description": "<div dir=\"auto\">Time to synergize!</div>",
    "description_attachments": [],
    "summary": "Team Meeting",
    "all_day": false,
    "starts_at": "2026-07-21T06:05:47.135Z",
    "ends_at": "2026-07-21T10:05:47.135Z",
    "participants": [
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
      }
    ]
  }
]
```
<!-- END GET /schedules/3/entries.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/schedules/3/entries.json
```


Get a schedule entry
--------------------

* `GET /schedule_entries/2.json` will return the schedule entry with an ID of `2`.

**Note:** this endpoint redirects to the first individual occurrence of the entry, for **recurring schedule entries**. It's also possible to access a recurring schedule entry via any of the individual occurrences: `GET /schedule_entries/2/occurrences/20190218.json` will return the occurrence for a recurring schedule entry with an ID of `2`, happening on `2019-02-18`. It'll return 404 for invalid occurrences.

###### Example JSON Response
<!-- START GET /schedule_entries/2.json -->
```json
{
  "id": 1069480280,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-28T17:29:04.741Z",
  "updated_at": "2026-05-28T17:29:04.965Z",
  "title": "Team Meeting",
  "inherits_status": true,
  "type": "Schedule::Entry",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/schedule_entries/1069480280.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/schedule_entries/1069480280",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI4MD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--da128107535b57443e391ebc9ce03a6d5c2097a8.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480280/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480280/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480280/boosts.json",
  "parent": {
    "id": 1069479831,
    "title": "Calendar",
    "type": "Schedule",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/schedules/1069479831.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/schedules/1069479831"
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
  "description": "<div dir=\"auto\">Time to synergize!</div>",
  "description_attachments": [],
  "summary": "Team Meeting",
  "all_day": false,
  "starts_at": "2026-07-21T06:05:47.135Z",
  "ends_at": "2026-07-21T10:05:47.135Z",
  "participants": [
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
    }
  ]
}
```
<!-- END GET /schedule_entries/2.json -->

Recurring schedule entries will include an additional `recurrence_schedule` attribute. For example:

```json
"recurrence_schedule": {
    "frequency": "every_month",
    "days": [
        1
    ],
    "hour": 10,
    "minute": 30,
    "week_instance": 3,
    "start_date": "2019-02-18",
    "end_date": "2019-10-25"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/schedule_entries/2.json
```


Create a schedule entry
-----------------------

* `POST /schedules/3/entries.json` creates a schedule entry under the schedule with an ID of `3`.

**Required parameters**:

* `summary` - what this schedule entry is about
* `starts_at` - date-time (ISO 8601) for when this schedule entry begins
* `ends_at` - date-time (ISO 8601) for when this schedule entry ends

_Optional parameters_:

* `description` - containing more information about the schedule entry. See our [Rich text guide][rich] for what HTML tags allowed.
* `participant_ids` - an array of people IDs that will participate in this entry. Please see the [Get people][people] endpoints to retrieve them.
* `all_day` - when set to `true`, the schedule entry will not have a specific start or end time, and instead will be held for the entire day or days denoted in `starts_at` and `ends_at`
* `notify` - when set to `true`, will notify the participants about the entry
* `recurrence_schedule` - makes the entry recurring. An object with:
  * `frequency` - one of `every_day`, `every_weekday`, `every_week`, `every_other_week`, `every_month`, `every_day_of_month`, `every_year`, `custom_week`, or `custom_month`
  * `days` - for `every_day`: which days of the week to recur on, as integers `0` (Sunday) through `6` (Saturday); omit to recur every day. For `custom_month` without a `week_instance`: which day of the month to recur on, `1` to `31`. Derived from `starts_at` for the other frequencies.
  * `week_instance` - for `every_month` and `custom_month`: which week of the month, `1` to `4`, or `-1` for the last week
  * `week_interval` - for `custom_week`: repeat every `2` to `12` weeks
  * `month_interval` - for `custom_month`: repeat every `2` to `12` months
* `recurs_until` - date (ISO 8601) the recurrence ends. Omit to recur indefinitely. Reflected as `recurrence_schedule.end_date` in the response.
* `visible_to_clients` - top-level boolean. When the project has clients enabled, whether the schedule entry is visible to them. Defaults to `false` (team callers creating directly under the docked tool); a **client** caller always creates client-visible records. See [Client visibility][client_visibility] to change it after creation.

The remaining `recurrence_schedule` attributes shown in [Get a schedule entry](#get-a-schedule-entry) (`hour`, `minute`, `start_date`, `duration`, `end_date`) are derived from `starts_at`, `ends_at`, and `recurs_until` — they're ignored on input. An invalid `recurrence_schedule` is discarded on create: the entry is created without recurring.

This endpoint will return `201 Created` with the current JSON representation of the schedule entry if the creation was a success. See the [Get a schedule entry](#get-a-schedule-entry) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "summary": "Important Meeting",
  "starts_at": "2015-06-04T00:00:00Z",
  "ends_at": "2015-06-04T02:00:00Z"
}
```

###### Example JSON Request (recurring)

```json
{
  "summary": "Weekly sync",
  "starts_at": "2015-06-04T15:00:00Z",
  "ends_at": "2015-06-04T16:00:00Z",
  "recurrence_schedule": { "frequency": "every_week" },
  "recurs_until": "2015-12-18"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"summary":"Important Meeting","starts_at":"2015-06-04T00:00:00Z","ends_at":"2015-06-04T02:00:00Z"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/schedules/3/entries.json
```


Update a schedule entry
-----------------------

* `PUT /schedule_entries/2.json` allows changing of the schedule entry with an ID of `2`.

Clients may change any of the required or optional parameters as listed in the [Create a schedule entry](#create-a-schedule-entry) endpoint. That includes adding a `recurrence_schedule` to make a non-recurring entry recur. An entry that already recurs can't be changed through this endpoint, though: it redirects to the entry's first occurrence, like [Get a schedule entry](#get-a-schedule-entry) does.

This endpoint will return `200 OK` with the current JSON representation of the schedule entry if the update was a success. See the [Get a schedule entry](#get-a-schedule-entry) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "summary": "All Day Meeting",
  "starts_at": "2015-06-04",
  "ends_at": "2015-06-04",
  "all_day": true
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"summary":"All Day Meeting","starts_at":"2015-06-04","ends_at":"2015-06-04","all_day":true}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/schedule_entries/2.json
```


Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/schedules/3/entries.json` → [Get schedule entries](#get-schedule-entries)
* `GET /buckets/1/schedule_entries/2.json` → [Get a schedule entry](#get-a-schedule-entry)
* `POST /buckets/1/schedules/3/entries.json` → [Create a schedule entry](#create-a-schedule-entry)
* `PUT /buckets/1/schedule_entries/2.json` → [Update a schedule entry](#update-a-schedule-entry)

[trash]: recordings.md#trash-a-recording
[pagination]: ../README.md#pagination
[schedule]: schedules.md#get-schedule
[rich]: rich_text.md
[people]: people.md#people
[client_visibility]: client_visibility.md
