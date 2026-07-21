Card table columns
================

Endpoints:

- [Get a column](#get-a-column)
- [Create a column](#create-a-column)
- [Update a column](#update-a-column)
- [Move a column](#move-a-column)
- [Watch a column](#watch-a-column)
- [Change on hold on a column](#change-on-hold-on-a-column)
- [Change color of a column](#change-color-of-a-column)

Get a column
-------------

* `GET /card_tables/columns/2.json` will return the column with an ID of `2`.

###### Example JSON Response
<!-- START GET /card_tables/columns/2.json -->
```json
{
  "id": 1069479834,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-28T17:23:17.411Z",
  "updated_at": "2026-05-28T17:23:29.745Z",
  "title": "Triage",
  "inherits_status": true,
  "type": "Kanban::Triage",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/columns/1069479834.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/columns/1069479834",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgzND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--44239f0fef95aba53d92f958278965ef8e9959c5.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479834/subscription.json",
  "parent": {
    "id": 1069479833,
    "title": "Card Table",
    "type": "Kanban::Board",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/1069479833.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/1069479833"
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
  "description": null,
  "subscribers": [
    {
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
    }
  ],
  "color": null,
  "cards_count": 1,
  "comment_count": 0,
  "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/lists/1069479834/cards.json"
}
```
<!-- END GET /card_tables/columns/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/card_tables/columns/2.json
```

Create a column
-------------------------

* `POST /card_tables/2/columns.json` creates a column within the card table with ID `2`.

**Required parameters**: `title` of the column.

_Optional parameters_:

* `description` - containing information about the column.

This endpoint will return `201 Created` with the current JSON representation of the column if the creation was a success. See the [Get a column](#get-a-column) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "title": "In progress",
  "description": "Stuff we are working on actively"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"title":"In progress"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/card_tables/2/columns.json
```

Update a column
-----------------------

* `PUT /card_tables/columns/2.json` allows changing of the column with an ID of `2`.

This endpoint will return `200 OK` with the current JSON representation of the column if the update was a success. See the [Get a column](#get-a-column) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "title": "On it",
  "description": "Stuff we are doing right now"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"title":"On it", "description":"Stuff we are doing right now"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/card_tables/columns/2.json
```

Move a column
-----------------------

* `POST /card_tables/2/moves.json` allows moving of a column in the card table with id `2`.

**Required parameters**:

* `source_id` - the id of the column to move
* `target_id` - the id of the card table

_Optional parameters_:

* `position` - index among the columns (ignoring Triage, Not Now or Done). Default: `1`

This endpoint will return `204 No Content` if the update was a success.

###### Example JSON Request

```json
{
  "source_id": 3,
  "target_id": 4,
  "position": 2
}
```
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"source_id": 3, "target_id":4, "position": 2}' \
  https://3.basecampapi.com/$ACCOUNT_ID/card_tables/2/moves.json
```

Watch a column
-----------------------
* `POST /card_tables/lists/2/subscription.json` starts watching the column with id `2`.
* `DELETE /card_tables/lists/2/subscription.json` stops watching the column with id `2`.

This endpoint will return `204 No Content` if the update was a success.

###### Copy as cURL
```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/card_tables/lists/2/subscription.json
```
```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/card_tables/lists/2/subscription.json
```

Change on hold on a column
-----------------------

* `POST /card_tables/columns/2/on_hold.json` creates an on_hold section in the column with ID `2`.
* `DELETE /card_tables/columns/2/on_hold.json` removes an on_hold section in the column with ID `2`.

This endpoint will return `200 OK` with the current JSON representation of the column if the operation was a success. See the [Get a column](#get-a-column) endpoint for more info on the payload.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/card_tables/columns/2/on_hold.json
```
```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/card_tables/columns/2/on_hold.json
```

Change color of a column
-----------------------

* `PUT /card_tables/columns/2/color.json` allows changing the color of the column with an ID of `2`.

This endpoint will return `200 OK` with the current JSON representation of the column if the update was a success. See the [Get a column](#get-a-column) endpoint for more info on the payload.


**Required parameters**:

* `color` - the color. Available values: `[ white red orange yellow green blue aqua purple gray pink brown ]`

###### Example JSON Request

```json
{
  "color": "orange"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"color":"orange"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/card_tables/columns/2/color.json
```

Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/card_tables/columns/2.json` → [Get a column](#get-a-column)
* `POST /buckets/1/card_tables/2/columns.json` → [Create a column](#create-a-column)
* `PUT /buckets/1/card_tables/columns/2.json` → [Update a column](#update-a-column)
* `POST /buckets/1/card_tables/2/moves.json` → [Move a column](#move-a-column)
* `POST /buckets/1/card_tables/lists/2/subscription.json` → [Watch a column](#watch-a-column)
* `DELETE /buckets/1/card_tables/lists/2/subscription.json` → [Watch a column](#watch-a-column)
* `POST /buckets/1/card_tables/columns/2/on_hold.json` → [Change on hold on a column](#change-on-hold-on-a-column)
* `DELETE /buckets/1/card_tables/columns/2/on_hold.json` → [Change on hold on a column](#change-on-hold-on-a-column)
* `PUT /buckets/1/card_tables/columns/2/color.json` → [Change color of a column](#change-color-of-a-column)
