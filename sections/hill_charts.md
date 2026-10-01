Hill charts
===========

Hill charts visualize the progress of to-do lists on a hill-shaped curve, from "figuring things out" (uphill) to "making it happen" (downhill). Each tracked to-do list appears as a dot on the hill.

Hill charts belong to a [to-do set][2]. To get the to-do set ID for a project, see the [Get a project][1] endpoint's `dock` payload.

Each time someone updates a hill chart, Basecamp saves a progress update: the note they wrote and where each to-do list sat on the hill at that moment. Earlier updates are kept, so the list of progress updates is the hill chart's history.

Endpoints:

- [Get hill chart](#get-hill-chart)
- [Get hill chart progress updates](#get-hill-chart-progress-updates)
- [Get a hill chart progress update](#get-a-hill-chart-progress-update)
- [Update hill chart settings](#update-hill-chart-settings)


Get hill chart
--------------

* `GET /todosets/1/hill.json` will return the hill chart for the to-do set with an ID of `1`.

###### Example JSON Response
<!-- START GET /todosets/1/hill.json -->
```json
{
  "enabled": true,
  "stale": false,
  "updated_at": "2026-07-21T00:01:19.857Z",
  "app_update_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829/hill/edit",
  "versions_url": "https://3.basecampapi.com/195539477/buckets/2085958505/todosets/1069479829/hills/versions.json",
  "app_versions_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829/hills/versions",
  "dots": [
    {
      "id": 1069479863,
      "label": "Background and research",
      "color": "blue",
      "position": 0,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479863.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479863"
    }
  ]
}
```
<!-- END GET /todosets/1/hill.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/todosets/1/hill.json
```


Get hill chart progress updates
-------------------------------

* `GET /todosets/1/hills/versions.json` will return a [paginated list][pagination] of progress updates for the hill chart of the to-do set with an ID of `1`, newest first.

Each progress update includes:

* `description` - the full note, as [rich text][3].
* `dots` - where each tracked to-do list sat on the hill when the update was made. `id` is the to-do list's ID, `label` is the list's full name at the time of the update, and `position` is on the same `0`–`100` scale as the hill chart's `dots`. If the to-do list has since been permanently deleted, `id` is `null` and `url` and `app_url` are omitted.
* `comments_count` and `comments_url` - discussion on the update. See [Get comments][4].

The hill chart JSON includes `versions_url` when the hill chart has any progress updates.

To collect progress updates across all projects, for example for a weekly review, use the [progress report][5]: events with a `kind` of `hill_version_created` have a `url` that returns the full progress update.

###### Example JSON Response
<!-- START GET /todosets/1/hills/versions.json -->
```json
[
  {
    "id": 1069480194,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-10-01T15:10:47.717Z",
    "updated_at": "2026-10-01T15:10:47.740Z",
    "title": "Hill Chart: Progress update",
    "inherits_status": true,
    "type": "Hill::Version",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todosets/1069479829/hills/versions/1069480194.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829/hills/versions#__recording_1069480194",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDE5ND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--0a88b14af225cad8f5b204fe79773cff49fc0f83.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480194/subscription.json",
    "comments_count": 0,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480194/comments.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480194/boosts.json",
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
      "id": 1049715913,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
      "name": "Victor Cooper",
      "personable_type": "User",
      "title": "Chief Strategist",
      "tagline": "Don't let your dreams be dreams",
      "location": "Chicago, IL",
      "created_at": "2026-10-01T15:09:21.537Z",
      "updated_at": "2026-10-01T15:09:22.123Z",
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
    "description": "<div dir=\"auto\">Research is wrapping up. We've settled on the approach and start building next week.</div>",
    "description_attachments": [],
    "dots": [
      {
        "id": 1069479863,
        "label": "Background and research",
        "color": "blue",
        "position": 40,
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479863.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479863"
      }
    ]
  }
]
```
<!-- END GET /todosets/1/hills/versions.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/todosets/1/hills/versions.json
```


Get a hill chart progress update
--------------------------------

* `GET /todosets/1/hills/versions/2.json` will return the progress update with an ID of `2` from the hill chart of the to-do set with an ID of `1`.

###### Example JSON Response
<!-- START GET /todosets/1/hills/versions/2.json -->
```json
{
  "id": 1069480194,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-10-01T15:10:47.717Z",
  "updated_at": "2026-10-01T15:10:47.740Z",
  "title": "Hill Chart: Progress update",
  "inherits_status": true,
  "type": "Hill::Version",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todosets/1069479829/hills/versions/1069480194.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829/hills/versions#__recording_1069480194",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDE5ND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--0a88b14af225cad8f5b204fe79773cff49fc0f83.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480194/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480194/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480194/boosts.json",
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
    "id": 1049715913,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
    "name": "Victor Cooper",
    "personable_type": "User",
    "title": "Chief Strategist",
    "tagline": "Don't let your dreams be dreams",
    "location": "Chicago, IL",
    "created_at": "2026-10-01T15:09:21.537Z",
    "updated_at": "2026-10-01T15:09:22.123Z",
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
  "description": "<div dir=\"auto\">Research is wrapping up. We've settled on the approach and start building next week.</div>",
  "description_attachments": [],
  "dots": [
    {
      "id": 1069479863,
      "label": "Background and research",
      "color": "blue",
      "position": 40,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479863.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479863"
    }
  ]
}
```
<!-- END GET /todosets/1/hills/versions/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/todosets/1/hills/versions/2.json
```


Update hill chart settings
--------------------------

* `PUT /todosets/1/hills/settings.json` allows tracking and untracking to-do lists on the hill chart for the to-do set with an ID of `1`.

Pass to-do list IDs to `tracked` and/or `untracked` arrays. Both are optional; you can track, untrack, or do both in a single request. Tracking the first to-do list enables the hill chart. Untracking the last to-do list disables it.

_Optional parameters_:

* `tracked` - an array of to-do list IDs to start tracking on the hill chart.
* `untracked` - an array of to-do list IDs to stop tracking on the hill chart.

Returns `200 OK` with the updated [hill chart](#get-hill-chart) JSON representation.

###### Example JSON Request

```json
{
  "tracked": [1069479573],
  "untracked": [1069479511]
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"tracked": [1069479573]}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/todosets/1/hills/settings.json
```


[1]: projects.md#get-a-project
[2]: todosets.md#get-to-do-set
[3]: rich_text.md
[4]: comments.md#get-comments
[5]: timeline.md#get-timeline
[pagination]: ../README.md#pagination
