Campfires
=========

Endpoints:

- [Get Campfires](#get-campfires)
- [Get a Campfire](#get-a-campfire)
- [Get Campfire lines](#get-campfire-lines)
- [Get a Campfire line](#get-a-campfire-line)
- [Create a Campfire line](#create-a-campfire-line)
- [Get Campfire uploads](#get-campfire-uploads)
- [Upload a file to a Campfire](#upload-a-file-to-a-campfire)
- [Delete a Campfire line](#delete-a-campfire-line)

Get Campfires
-------------

* `GET /chats.json` will return a [paginated list][pagination] of all active Campfires visible to the current user.

###### Example JSON Response
<!-- START GET /chats.json -->
```json
[
  {
    "id": 1069478958,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-05-28T17:22:34.182Z",
    "updated_at": "2026-07-21T00:06:30.556Z",
    "title": "Chat",
    "inherits_status": true,
    "type": "Chat::Transcript",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3ODk1OD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--46b0cba4fd8326b694d7c6965987aa2f3cd68e8e.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069478958/subscription.json",
    "position": 5,
    "bucket": {
      "id": 2085958502,
      "name": "Honcho Design Newsroom",
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
    "topic": "Chat",
    "lines_url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958/lines.json",
    "files_url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958/uploads.json"
  }
]
```
<!-- END GET /chats.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/chats.json
```

Get a Campfire
--------------

* `GET /chats/2.json` will return the Campfire with ID `2`.

###### Example JSON Response
<!-- START GET /chats/2.json -->
```json
{
  "id": 1069478958,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-28T17:22:34.182Z",
  "updated_at": "2026-07-21T00:06:30.556Z",
  "title": "Chat",
  "inherits_status": true,
  "type": "Chat::Transcript",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3ODk1OD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--46b0cba4fd8326b694d7c6965987aa2f3cd68e8e.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069478958/subscription.json",
  "position": 5,
  "bucket": {
    "id": 2085958502,
    "name": "Honcho Design Newsroom",
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
  "topic": "Chat",
  "lines_url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958/lines.json",
  "files_url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958/uploads.json"
}
```
<!-- END GET /chats/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/chats/2.json
```

Get Campfire lines
------------------

* `GET /chats/2/lines.json` will return a [paginated list][pagination] of Campfire lines of the Campfire with ID `2`.

###### Example JSON Response
<!-- START GET /chats/2/lines.json -->
```json
[
  {
    "id": 1069479442,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-03-12T16:43:00.000Z",
    "updated_at": "2026-03-12T16:43:00.000Z",
    "title": "Words to live by",
    "inherits_status": true,
    "type": "Chat::Lines::RichText",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958/lines/1069479442.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958@1069479442",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTQ0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--7c9b636ccce44a15856664e701b0f8b4b4215dcf.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479442/boosts.json",
    "parent": {
      "id": 1069478958,
      "title": "Chat",
      "type": "Chat::Transcript",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958"
    },
    "bucket": {
      "id": 2085958502,
      "name": "Honcho Design Newsroom",
      "type": "Project"
    },
    "creator": {
      "id": 1049715923,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkyMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--cd47d2c8e0331392dba60ca41aec78611b6f2f2e",
      "name": "Jerry Gibson",
      "personable_type": "User",
      "title": "Principal Configuration Planner",
      "tagline": null,
      "location": null,
      "created_at": "2026-05-28T17:22:25.855Z",
      "updated_at": "2026-05-28T17:22:25.855Z",
      "email_address": "jerry@honchodesign.com",
      "bio": null,
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNNkkT4=--e3c2676dde30e7c13f87642e3a3dd46ad657f731/avatar",
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    },
    "content": "Words to live by"
  }
]
```
<!-- END GET /chats/2/lines.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/chats/2/lines.json
```

Get a Campfire line
-------------------

* `GET /chats/2/lines/3.json` will return the Campfire line with ID `3` in the Campfire with ID `2`.

###### Example JSON Response
<!-- START GET /chats/2/lines/3.json -->
```json
{
  "id": 1069479428,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-03-12T06:49:00.000Z",
  "updated_at": "2026-03-12T06:49:00.000Z",
  "title": "Hey quick heads up: CI is running slow today",
  "inherits_status": true,
  "type": "Chat::Lines::RichText",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958/lines/1069479428.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958@1069479428",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTQyOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--678075872f6cdf26d765ca03f9d314b7986d90ba.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479428/boosts.json",
  "parent": {
    "id": 1069478958,
    "title": "Chat",
    "type": "Chat::Transcript",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958"
  },
  "bucket": {
    "id": 2085958502,
    "name": "Honcho Design Newsroom",
    "type": "Project"
  },
  "creator": {
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
  "content": "Hey quick heads up: CI is running slow today"
}
```
<!-- END GET /chats/2/lines/3.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/chats/2/lines/3.json
```

Create a Campfire line
----------------------

* `POST /chats/2/lines.json` creates a line in the Campfire with ID `2`.

**Required parameters**: `content` as the body for the Campfire line.

_Optional parameters_:

* `content_type` - set to `text/html` to create a rich text line. Default: plain text.

This endpoint will return `201 Created` with the current JSON representation of the line if the creation was a success. See the [Get a Campfire line](#get-a-campfire-line) endpoint for more info on the payload.

###### Example JSON Request (plain text)

```json
{
  "content": "Good morning"
}
```

###### Example JSON Request (rich text)

```json
{
  "content": "<strong>Hello</strong> from the API",
  "content_type": "text/html"
}
```

###### Example JSON Response (plain text)
<!-- START POST /buckets/1/chats/2/lines.json -->
```json
{
  "id": 1069480439,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-07-21T01:06:27.525Z",
  "updated_at": "2026-07-21T01:06:27.525Z",
  "title": "Good morning",
  "inherits_status": true,
  "type": "Chat::Lines::Text",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958/lines/1069480439.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958@1069480439",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDQzOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--f588fd67e33dc0c260197317a9e06a456b3c4d26.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069480439/boosts.json",
  "parent": {
    "id": 1069478958,
    "title": "Chat",
    "type": "Chat::Transcript",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958"
  },
  "bucket": {
    "id": 2085958502,
    "name": "Honcho Design Newsroom",
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
  "content": "Good morning"
}
```
<!-- END POST /buckets/1/chats/2/lines.json -->

###### Example JSON Response (rich text)
<!-- START POST /buckets/1/chats/2/lines.json (rich text) -->
```json
{
  "id": 1069480440,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-07-21T01:06:28.175Z",
  "updated_at": "2026-07-21T01:06:28.175Z",
  "title": "Hello from the API",
  "inherits_status": true,
  "type": "Chat::Lines::RichText",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958/lines/1069480440.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958@1069480440",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDQ0MD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--b8623294d1d1f9b7f24d9d6d6639f2725b4c7200.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069480440/boosts.json",
  "parent": {
    "id": 1069478958,
    "title": "Chat",
    "type": "Chat::Transcript",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958"
  },
  "bucket": {
    "id": 2085958502,
    "name": "Honcho Design Newsroom",
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
    "updated_at": "2026-07-20T20:06:02.483-05:00",
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
  "content": "<strong>Hello</strong> from the API"
}
```
<!-- END POST /buckets/1/chats/2/lines.json (rich text) -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"content":"Good morning"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/chats/2/lines.json
```

Get Campfire uploads
--------------------

* `GET /chats/2/uploads.json` will return a [paginated list][pagination] of file uploads in the Campfire with ID `2`, sorted newest first.

###### Example JSON Response
<!-- START GET /chats/2/uploads.json -->
```json
[
  {
    "id": 1069480441,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-07-21T01:06:29.159Z",
    "updated_at": "2026-07-21T01:06:29.228Z",
    "title": "company-logo.png",
    "inherits_status": true,
    "type": "Chat::Lines::Upload",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958/lines/1069480441.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958@1069480441",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDQ0MT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--d5c8bfc9c08196e1475b641e6444f2cb95d00ef3.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069480441/boosts.json",
    "parent": {
      "id": 1069478958,
      "title": "Chat",
      "type": "Chat::Transcript",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958"
    },
    "bucket": {
      "id": 2085958502,
      "name": "Honcho Design Newsroom",
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
      "updated_at": "2026-07-20T20:06:02.483-05:00",
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
    "attachments": [
      {
        "title": "company-logo.png",
        "url": "https://3.basecampapi.com/195539477/blobs/b092e1a5f8192edc092f7acc644142725ce5e65c/previews/full",
        "filename": "company-logo.png",
        "content_type": "image/png",
        "byte_size": 1281,
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/b092e1a5f8192edc092f7acc644142725ce5e65c/download/company-logo.png"
      }
    ]
  }
]
```
<!-- END GET /chats/2/uploads.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/chats/2/uploads.json
```

Upload a file to a Campfire
----------------------------

* `POST /chats/2/uploads.json` uploads a file to the Campfire with ID `2`.

**Required request data**: The request body should be the file's raw binary data.

**Required request headers**: `Content-Type` and `Content-Length` for the file.

**Required URI query parameters**: `name` as the file name.

This endpoint will return `201 Created` with the current JSON representation of the upload line if the creation was a success. Each upload line contains an `attachments` array with `title`, `filename`, `content_type`, `byte_size`, `url`, and `download_url` for each file.

###### Example JSON Response
<!-- START POST /chats/2/uploads.json -->
```json
{
  "id": 1069480441,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-07-21T01:06:29.159Z",
  "updated_at": "2026-07-21T01:06:29.228Z",
  "title": "company-logo.png",
  "inherits_status": true,
  "type": "Chat::Lines::Upload",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958/lines/1069480441.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958@1069480441",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDQ0MT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--d5c8bfc9c08196e1475b641e6444f2cb95d00ef3.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069480441/boosts.json",
  "parent": {
    "id": 1069478958,
    "title": "Chat",
    "type": "Chat::Transcript",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958"
  },
  "bucket": {
    "id": 2085958502,
    "name": "Honcho Design Newsroom",
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
    "updated_at": "2026-07-20T20:06:02.483-05:00",
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
  "attachments": [
    {
      "title": "company-logo.png",
      "url": "https://3.basecampapi.com/195539477/blobs/b092e1a5f8192edc092f7acc644142725ce5e65c/previews/full",
      "filename": "company-logo.png",
      "content_type": "image/png",
      "byte_size": 1281,
      "download_url": "https://storage.3.basecamp.com/195539477/blobs/b092e1a5f8192edc092f7acc644142725ce5e65c/download/company-logo.png"
    }
  ]
}
```
<!-- END POST /chats/2/uploads.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  --data-binary @logo.png \
  -H "Content-Type: image/png" -H "Content-Length: 1281" \
  https://3.basecampapi.com/$ACCOUNT_ID/chats/2/uploads.json?name=logo.png
```

Delete a Campfire line
----------------------

* `DELETE /chats/2/lines/3.json` will delete the Campfire line with ID `3` in the Campfire with ID `2`.

Returns `204 No Content` if successful.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/chats/2/lines/3.json
```

Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/chats/2.json` → [Get a Campfire](#get-a-campfire)
* `GET /buckets/1/chats/2/lines.json` → [Get Campfire lines](#get-campfire-lines)
* `GET /buckets/1/chats/2/lines/3.json` → [Get a Campfire line](#get-a-campfire-line)
* `POST /buckets/1/chats/2/lines.json` → [Create a Campfire line](#create-a-campfire-line)
* `GET /buckets/1/chats/2/uploads.json` → [Get Campfire uploads](#get-campfire-uploads)
* `POST /buckets/1/chats/2/uploads.json` → [Upload a file to a Campfire](#upload-a-file-to-a-campfire)
* `DELETE /buckets/1/chats/2/lines/3.json` → [Delete a Campfire line](#delete-a-campfire-line)

[pagination]: ../README.md#pagination
