Gauges
======

Gauges visualize the overall progress of a project with a needle position (0–100), a color indicator (green, yellow, or red), and an optional description. Each time progress is recorded, a new gauge needle is created, preserving a history of updates.

Gauges are automatically created when a project is created. To check whether a project has gauge data, look for the `last_needle_color` and `last_needle_position` attributes on the [project][projects] JSON response.

Endpoints:

- [Get gauges](#get-gauges)
- [Get gauge needles](#get-gauge-needles)
- [Get a gauge needle](#get-a-gauge-needle)
- [Create a gauge needle](#create-a-gauge-needle)
- [Update a gauge needle](#update-a-gauge-needle)
- [Destroy a gauge needle](#destroy-a-gauge-needle)
- [Toggle a gauge](#toggle-a-gauge)


Get gauges
----------

* `GET /reports/gauges.json` will return a [paginated list][pagination] of gauges across all projects the authenticated user has access to. Gauges are sorted by risk level (red → yellow → green), then alphabetically by project name.

_Optional parameters_:

* `bucket_ids` - a comma-separated list of project IDs. When provided, results are returned in the order specified instead of by risk level.

###### Example JSON Response
<!-- START GET /reports/gauges.json -->
```json
[
  {
    "id": 1069479405,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-03-14T00:47:12.714Z",
    "updated_at": "2026-03-14T02:10:01.171Z",
    "title": "How far along are we?",
    "inherits_status": true,
    "type": "Gauge",
    "url": "https://3.basecampapi.com/195539477/projects/2085958504/gauge.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958504/gauge",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTQwNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--3a34a17d068adfa8cd7cfdbefef53a07ecea0d9d.json",
    "bucket": {
      "id": 2085958504,
      "name": "The Leto Laptop",
      "type": "Project"
    },
    "creator": {
      "id": 1049715913,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
      "name": "Victor Cooper",
      "email_address": "victor@honchodesign.com",
      "personable_type": "User",
      "title": "Chief Strategist",
      "bio": "Don’t let your dreams be dreams",
      "location": "Chicago, IL",
      "created_at": "2026-03-14T00:46:56.489Z",
      "updated_at": "2026-03-14T00:46:57.021Z",
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
      "can_access_timesheet": false,
      "can_access_hill_charts": true
    },
    "description": "Design phase wrapping up, development starting next week",
    "enabled": true,
    "last_needle_color": "yellow",
    "last_needle_position": 42,
    "previous_needle_position": null
  }
]
```
<!-- END GET /reports/gauges.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/reports/gauges.json
```


Get gauge needles
-----------------

* `GET /projects/1/gauge/needles.json` will return a [paginated list][pagination] of gauge needles for the project with an ID of `1`, ordered newest first.

###### Example JSON Response
<!-- START GET /projects/1/gauge/needles.json -->
```json
[
  {
    "id": 1069479928,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-03-14T02:10:01.131Z",
    "updated_at": "2026-03-14T02:10:01.141Z",
    "title": "Moved the needle",
    "inherits_status": true,
    "type": "Gauge::Needle",
    "url": "https://3.basecampapi.com/195539477/projects/2085958504/gauge/needles/1069479928.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958504/gauge/needles/1069479928",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTkyOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--8031593b95d6a0cf3158ccd092686ec3e4bd3f59.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479928/subscription.json",
    "comments_count": 0,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479928/comments.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479928/boosts.json",
    "parent": {
      "id": 1069479405,
      "title": "How far along are we?",
      "type": "Gauge",
      "url": "https://3.basecampapi.com/195539477/projects/2085958504/gauge.json",
      "app_url": "https://3.basecamp.com/195539477/projects/2085958504/gauge"
    },
    "bucket": {
      "id": 2085958504,
      "name": "The Leto Laptop",
      "type": "Project"
    },
    "creator": {
      "id": 1049715913,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
      "name": "Victor Cooper",
      "email_address": "victor@honchodesign.com",
      "personable_type": "User",
      "title": "Chief Strategist",
      "bio": "Don’t let your dreams be dreams",
      "location": "Chicago, IL",
      "created_at": "2026-03-14T00:46:56.489Z",
      "updated_at": "2026-03-14T00:46:57.021Z",
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
      "can_access_timesheet": false,
      "can_access_hill_charts": true
    },
    "description": "Design phase wrapping up, development starting next week",
    "color": "yellow",
    "position": 42,
    "comment_count": 0
  }
]
```
<!-- END GET /projects/1/gauge/needles.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/projects/1/gauge/needles.json
```


Get a gauge needle
------------------

* `GET /gauge_needles/2.json` will return the gauge needle with an ID of `2`.

###### Example JSON Response
<!-- START GET /gauge_needles/2.json -->
```json
{
  "id": 1069479928,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-03-14T02:10:01.131Z",
  "updated_at": "2026-03-14T02:10:01.141Z",
  "title": "Moved the needle",
  "inherits_status": true,
  "type": "Gauge::Needle",
  "url": "https://3.basecampapi.com/195539477/projects/2085958504/gauge/needles/1069479928.json",
  "app_url": "https://3.basecamp.com/195539477/projects/2085958504/gauge/needles/1069479928",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTkyOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--8031593b95d6a0cf3158ccd092686ec3e4bd3f59.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479928/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479928/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479928/boosts.json",
  "parent": {
    "id": 1069479405,
    "title": "How far along are we?",
    "type": "Gauge",
    "url": "https://3.basecampapi.com/195539477/projects/2085958504/gauge.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958504/gauge"
  },
  "bucket": {
    "id": 2085958504,
    "name": "The Leto Laptop",
    "type": "Project"
  },
  "creator": {
    "id": 1049715913,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
    "name": "Victor Cooper",
    "email_address": "victor@honchodesign.com",
    "personable_type": "User",
    "title": "Chief Strategist",
    "bio": "Don’t let your dreams be dreams",
    "location": "Chicago, IL",
    "created_at": "2026-03-14T00:46:56.489Z",
    "updated_at": "2026-03-14T00:46:57.021Z",
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
    "can_access_timesheet": false,
    "can_access_hill_charts": true
  },
  "description": "Design phase wrapping up, development starting next week",
  "color": "yellow",
  "position": 42,
  "comment_count": 0
}
```
<!-- END GET /gauge_needles/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/gauge_needles/2.json
```


Create a gauge needle
---------------------

* `POST /projects/1/gauge/needles.json` creates a gauge needle for the project with an ID of `1`.

**Required parameters**: `gauge_needle[position]` as an integer between 0 and 100.

_Optional parameters_:

* `gauge_needle[color]` - the status color: `green` (default), `yellow`, or `red`.
* `gauge_needle[description]` - a rich text (HTML) description of the progress update.
* `notify` - who to notify about this update: `default` (people subscribed to project notifications), `everyone`, `custom` (specific people via `subscriptions`), or omit to notify nobody.
* `subscriptions` - an array of people IDs to notify. Only used when `notify` is `custom`.

This endpoint will return `201 Created` with the JSON representation of the needle if the creation was a success. See the [Get a gauge needle](#get-a-gauge-needle) endpoint for more info on the payload.

###### Example JSON Response
<!-- START POST /projects/1/gauge/needles.json -->
```json
{
  "id": 1069479929,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-03-14T02:10:02.274Z",
  "updated_at": "2026-03-14T02:10:02.277Z",
  "title": "Moved the needle",
  "inherits_status": true,
  "type": "Gauge::Needle",
  "url": "https://3.basecampapi.com/195539477/projects/2085958504/gauge/needles/1069479929.json",
  "app_url": "https://3.basecamp.com/195539477/projects/2085958504/gauge/needles/1069479929",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTkyOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--43f9e0540b4d0f2448c284a3696a19024038b36c.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479929/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479929/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479929/boosts.json",
  "parent": {
    "id": 1069479405,
    "title": "How far along are we?",
    "type": "Gauge",
    "url": "https://3.basecampapi.com/195539477/projects/2085958504/gauge.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958504/gauge"
  },
  "bucket": {
    "id": 2085958504,
    "name": "The Leto Laptop",
    "type": "Project"
  },
  "creator": {
    "id": 1049715913,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
    "name": "Victor Cooper",
    "email_address": "victor@honchodesign.com",
    "personable_type": "User",
    "title": "Chief Strategist",
    "bio": "Don’t let your dreams be dreams",
    "location": "Chicago, IL",
    "created_at": "2026-03-14T00:46:56.489Z",
    "updated_at": "2026-03-14T00:46:57.021Z",
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
    "can_access_timesheet": false,
    "can_access_hill_charts": true
  },
  "description": "<div>Strong progress across all workstreams</div>",
  "color": "green",
  "position": 85,
  "comment_count": 0
}
```
<!-- END POST /projects/1/gauge/needles.json -->

###### Example JSON Request

```json
{
  "gauge_needle": {
    "position": 50,
    "color": "yellow",
    "description": "<div>Halfway there, some blockers on design review</div>"
  }
}
```

To notify specific people, pass `notify` set to `custom` alongside a `subscriptions` array of people IDs:

```json
{
  "gauge_needle": {
    "position": 50,
    "color": "yellow",
    "description": "<div>Halfway there, some blockers on design review</div>"
  },
  "notify": "custom",
  "subscriptions": [1049715914, 1049715916]
}
```

To notify everyone on the project, set `notify` to `everyone` (no `subscriptions` array needed):

```json
{
  "gauge_needle": {
    "position": 50,
    "color": "yellow",
    "description": "<div>Halfway there</div>"
  },
  "notify": "everyone"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"gauge_needle":{"position":50,"color":"yellow","description":"<div>Halfway there</div>"}}' \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/1/gauge/needles.json
```


Update a gauge needle
---------------------

* `PUT /gauge_needles/2.json` allows changing the description of the gauge needle with an ID of `2`.

**Note**: Only the description can be updated. The position and color are immutable after creation. To record a new progress update, create a new gauge needle instead — each needle represents a point-in-time snapshot.

_Optional parameters_:

* `gauge_needle[description]` - a rich text (HTML) description.

This endpoint will return `200 OK` with the JSON representation of the updated needle. See the [Get a gauge needle](#get-a-gauge-needle) endpoint for more info on the payload.

###### Example JSON Response
<!-- START PUT /gauge_needles/2.json -->
```json
{
  "id": 1069479929,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-03-14T02:10:02.274Z",
  "updated_at": "2026-03-14T02:10:02.618Z",
  "title": "Moved the needle",
  "inherits_status": true,
  "type": "Gauge::Needle",
  "url": "https://3.basecampapi.com/195539477/projects/2085958504/gauge/needles/1069479929.json",
  "app_url": "https://3.basecamp.com/195539477/projects/2085958504/gauge/needles/1069479929",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTkyOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--43f9e0540b4d0f2448c284a3696a19024038b36c.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479929/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479929/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479929/boosts.json",
  "parent": {
    "id": 1069479405,
    "title": "How far along are we?",
    "type": "Gauge",
    "url": "https://3.basecampapi.com/195539477/projects/2085958504/gauge.json",
    "app_url": "https://3.basecamp.com/195539477/projects/2085958504/gauge"
  },
  "bucket": {
    "id": 2085958504,
    "name": "The Leto Laptop",
    "type": "Project"
  },
  "creator": {
    "id": 1049715913,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
    "name": "Victor Cooper",
    "email_address": "victor@honchodesign.com",
    "personable_type": "User",
    "title": "Chief Strategist",
    "bio": "Don’t let your dreams be dreams",
    "location": "Chicago, IL",
    "created_at": "2026-03-14T00:46:56.489Z",
    "updated_at": "2026-03-14T00:46:57.021Z",
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
    "can_access_timesheet": false,
    "can_access_hill_charts": true
  },
  "description": "<div>Updated: design review complete, moving forward</div>",
  "color": "green",
  "position": 85,
  "comment_count": 0
}
```
<!-- END PUT /gauge_needles/2.json -->

###### Example JSON Request

```json
{
  "gauge_needle": {
    "description": "<div>Updated: design review complete, moving forward</div>"
  }
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"gauge_needle":{"description":"<div>Updated progress</div>"}}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/gauge_needles/2.json
```


Destroy a gauge needle
----------------------

* `DELETE /gauge_needles/2.json` will destroy the gauge needle with an ID of `2`.

Returns `204 No Content` on success.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/gauge_needles/2.json
```


Toggle a gauge
---------------

* `PUT /projects/1/gauge.json` enables or disables the gauge for the project with an ID of `1`.

**Required parameters**: `gauge[enabled]` as a boolean.

Returns `200 OK` on success with no response body. Only project admins can toggle gauges.

###### Example JSON Request

```json
{
  "gauge": {
    "enabled": false
  }
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"gauge":{"enabled":false}}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/1/gauge.json
```


Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /projects/1/gauge/needles.json` → [Get gauge needles](#get-gauge-needles)
* `GET /projects/1/gauge/needles/2.json` → [Get a gauge needle](#get-a-gauge-needle)
* `POST /projects/1/gauge/needles.json` → [Create a gauge needle](#create-a-gauge-needle)
* `PUT /projects/1/gauge/needles/2.json` → [Update a gauge needle](#update-a-gauge-needle)
* `DELETE /projects/1/gauge/needles/2.json` → [Destroy a gauge needle](#destroy-a-gauge-needle)

[projects]: projects.md#get-a-project
[pagination]: ../README.md#pagination
