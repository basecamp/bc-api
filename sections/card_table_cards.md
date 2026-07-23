Card table cards
================

Endpoints:

- [Get cards in a column](#get-cards-in-a-column)
- [Get a card](#get-a-card)
- [Create a card](#create-a-card)
- [Update a card](#update-a-card)
- [Move a card](#move-a-card)

Get cards in a column
--------------------

* `GET /card_tables/lists/3/cards.json` will return a [paginated list][pagination] of cards in the column with ID of `3`.

###### Example JSON Response
<!-- START GET /card_tables/lists/3/cards.json -->
```json
[
  {
    "id": 1069480041,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-05-14T21:00:00.000Z",
    "updated_at": "2026-05-28T17:23:29.744Z",
    "title": "New and fancy UI",
    "inherits_status": true,
    "type": "Kanban::Card",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/cards/1069480041.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/cards/1069480041",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDA0MT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--b4c3e9daec4a87607f8e0b9399bbc5bc335e1ee4.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480041/subscription.json",
    "comments_count": 0,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480041/comments.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480041/boosts.json",
    "position": 1,
    "parent": {
      "id": 1069479834,
      "title": "Triage",
      "type": "Kanban::Triage",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/columns/1069479834.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/columns/1069479834"
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
    "description": "Design a new and fancy UI",
    "description_attachments": [],
    "completed": false,
    "content": "Design a new and fancy UI",
    "due_on": null,
    "assignees": [],
    "completion_subscribers": [],
    "completion_url": "https://3.basecampapi.com/195539477/buckets/2085958505/todos/1069480041/completion.json",
    "comment_count": 0,
    "steps": [
      {
        "id": 1069480042,
        "status": "active",
        "visible_to_clients": false,
        "created_at": "2026-05-14T21:47:00.000Z",
        "updated_at": "2026-05-14T21:47:00.000Z",
        "title": "Find inspiration",
        "inherits_status": true,
        "type": "Kanban::Step",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/steps/1069480042.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/cards/1069480041#__recording_1069480042",
        "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDA0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--ac919964135c88e0b8d853cf2c2968095f8ce46a.json",
        "position": 1,
        "parent": {
          "id": 1069480041,
          "title": "New and fancy UI",
          "type": "Kanban::Card",
          "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/cards/1069480041.json",
          "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/cards/1069480041"
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
        "completed": false,
        "due_on": "2026-06-01",
        "assignees": [
          {
            "id": 1049715931,
            "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzMT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--0c0826b2c47fc879d171cb99aa564d38e5a54a67",
            "name": "Tashia Hughes",
            "personable_type": "User",
            "title": "District Integration Architect",
            "tagline": null,
            "location": null,
            "created_at": "2026-05-28T17:22:28.453Z",
            "updated_at": "2026-05-28T17:22:28.453Z",
            "email_address": "tashia@honchodesign.com",
            "bio": null,
            "admin": false,
            "owner": false,
            "client": false,
            "employee": false,
            "time_zone": "America/Chicago",
            "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNtkkT4=--b72a5df90f237e00570273b726a82176287186e4/avatar",
            "can_ping": true,
            "can_manage_projects": true,
            "can_manage_people": true,
            "can_access_timesheet": true,
            "can_access_hill_charts": true
          }
        ],
        "completion_url": "/195539477/buckets/2085958505/steps/1069480042/completions.json"
      }
    ]
  }
]
```
<!-- END GET /card_tables/lists/3/cards.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/card_tables/lists/3/cards.json
```

Get a card
--------------------

* `GET /card_tables/cards/2.json` will return the card with an ID of `2`.

###### Example JSON Response
<!-- START GET /card_tables/cards/2.json -->
```json
{
  "id": 1069480041,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-14T21:00:00.000Z",
  "updated_at": "2026-05-28T17:23:29.744Z",
  "title": "New and fancy UI",
  "inherits_status": true,
  "type": "Kanban::Card",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/cards/1069480041.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/cards/1069480041",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDA0MT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--b4c3e9daec4a87607f8e0b9399bbc5bc335e1ee4.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480041/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480041/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480041/boosts.json",
  "position": 1,
  "parent": {
    "id": 1069479834,
    "title": "Triage",
    "type": "Kanban::Triage",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/columns/1069479834.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/columns/1069479834"
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
  "description": "Design a new and fancy UI",
  "description_attachments": [],
  "completed": false,
  "content": "Design a new and fancy UI",
  "due_on": null,
  "assignees": [],
  "completion_subscribers": [],
  "completion_url": "https://3.basecampapi.com/195539477/buckets/2085958505/todos/1069480041/completion.json",
  "comment_count": 0,
  "steps": [
    {
      "id": 1069480042,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-05-14T21:47:00.000Z",
      "updated_at": "2026-05-14T21:47:00.000Z",
      "title": "Find inspiration",
      "inherits_status": true,
      "type": "Kanban::Step",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/steps/1069480042.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/cards/1069480041#__recording_1069480042",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDA0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--ac919964135c88e0b8d853cf2c2968095f8ce46a.json",
      "position": 1,
      "parent": {
        "id": 1069480041,
        "title": "New and fancy UI",
        "type": "Kanban::Card",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/cards/1069480041.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/cards/1069480041"
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
      "completed": false,
      "due_on": "2026-06-01",
      "assignees": [
        {
          "id": 1049715931,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzMT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--0c0826b2c47fc879d171cb99aa564d38e5a54a67",
          "name": "Tashia Hughes",
          "personable_type": "User",
          "title": "District Integration Architect",
          "tagline": null,
          "location": null,
          "created_at": "2026-05-28T17:22:28.453Z",
          "updated_at": "2026-05-28T17:22:28.453Z",
          "email_address": "tashia@honchodesign.com",
          "bio": null,
          "admin": false,
          "owner": false,
          "client": false,
          "employee": false,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNtkkT4=--b72a5df90f237e00570273b726a82176287186e4/avatar",
          "can_ping": true,
          "can_manage_projects": true,
          "can_manage_people": true,
          "can_access_timesheet": true,
          "can_access_hill_charts": true
        }
      ],
      "completion_url": "/195539477/buckets/2085958505/steps/1069480042/completions.json"
    }
  ]
}
```
<!-- END GET /card_tables/cards/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/card_tables/cards/2.json
```

Create a card
-------------------------

* `POST /card_tables/lists/2/cards.json` creates a card within the column with ID `2`.

**Required parameters**: `title` of the card.

_Optional parameters_:

* `content` - containing information about the card. See our [Rich text guide][rich] for what HTML tags are allowed.
* `due_on` - due date (ISO 8601) of the card
* `notify` - whether to notify assignees, value `true` or `false`. Defaults to `false`.

This endpoint will return `201 Created` with the current JSON representation of the card if the creation was a success. See the [Get a card](#get-a-card) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "title": "Investigation",
  "content": "Investigate on an issue in our todo list.",
  "due_on": "2021-01-01"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"title":"Investigation", "content": "Investigate on an issue in our todo list.", "due_on": "2021-01-01"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/card_tables/lists/2/cards.json
```

Update a card
-----------------------

* `PUT /card_tables/cards/2.json` allows changing of the card with an ID of `2`.

_Optional parameters_:

* `title` - of the card.
* `content` - containing information about the card. See our [Rich text guide][rich] for what HTML tags are allowed.
* `due_on` - due date (ISO 8601) of the card
* `assignee_ids` - an array of people that will be assigned to this to-do. Please see the [Get people][people] endpoints to retrieve them.

This endpoint will return `200 OK` with the current JSON representation of the card if the update was a success. See the [Get a card](#get-a-card) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "title": "Updated investigation"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"title":"Updated investigation"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/card_tables/cards/2.json
```

Move a card
-----------------------

* `POST /card_tables/cards/2/moves.json` allows moving of a card with id `2`.

**Required parameters**: `column_id` of the column destination

_Optional parameters_:

* `position` - 1-indexed position within the destination column. Defaults to `1`, placing the card at the top. Must be a positive integer.

This endpoint will return `204 No Content` if the move was a success. Returns `400 Bad Request` if `position` is zero, negative, or non-numeric.

Passing a [wormhole](card_table_wormholes.md)'s `id` as the `column_id` moves the card to **another card table**, including one in another project. A wormhole on the source card table points at a destination column on the other card table; create one with the [card table wormholes](card_table_wormholes.md) endpoints, or reuse a linked one already listed in the card table's `wormholes` array (see [Get a card table](card_tables.md#get-a-card-table)); the wormhole must be linked (`"linked": true`) and its destination reachable by the requester, so moving onto an unlinked or unreachable wormhole returns `404 Not Found`.

So the recipe is:

1. Create a wormhole on the source card table (id `2`) pointing at the destination column — `POST /buckets/1/card_tables/2/wormholes.json` with `{"destination_recording_id": <id of the destination column>}` — and capture the new wormhole's `id` from the `201 Created` response.
2. Move the card (id `2`) onto that wormhole — `POST /card_tables/cards/2/moves.json` with `{"column_id": <the wormhole's id>}`, expecting `204 No Content`.

The endpoint returns `204 No Content` once the teleport is queued. Completion is asynchronous; the response does not expose the destination card's new recording ID, and the original card ID returns `404 Not Found` after completion. `position` does not control a teleport's destination placement; if supplied, it must still be a positive integer. Placement is determined when the move completes.

###### Example JSON Request

```json
{
  "column_id": 3,
  "position": 2
}
```
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"column_id": 3, "position": 2}' \
  https://3.basecampapi.com/$ACCOUNT_ID/card_tables/cards/2/moves.json
```


Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/card_tables/lists/3/cards.json` → [Get cards in a column](#get-cards-in-a-column)
* `GET /buckets/1/card_tables/cards/2.json` → [Get a card](#get-a-card)
* `POST /buckets/1/card_tables/lists/2/cards.json` → [Create a card](#create-a-card)
* `PUT /buckets/1/card_tables/cards/2.json` → [Update a card](#update-a-card)
* `POST /buckets/1/card_tables/cards/2/moves.json` → [Move a card](#move-a-card)

[pagination]: ../README.md#pagination
[rich]: rich_text.md
[people]: people.md#get-all-people
