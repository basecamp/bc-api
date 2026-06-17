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
    "id": 1069478985,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-03-23T22:12:38.539Z",
    "updated_at": "2026-03-23T22:12:44.024Z",
    "title": "Chat",
    "inherits_status": true,
    "type": "Chat::Transcript",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3ODk4NT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--f745f0a5dc8108b7f361e578d47b72ff974ed50e.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069478985/subscription.json",
    "position": 4,
    "bucket": {
      "id": 2085958502,
      "name": "Honcho Design Newsroom",
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
      "created_at": "2026-03-23T22:12:24.947Z",
      "updated_at": "2026-03-23T22:12:26.266Z",
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
    "lines_url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985/lines.json",
    "files_url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985/uploads.json"
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
  "id": 1069478985,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-03-23T22:12:38.539Z",
  "updated_at": "2026-03-23T22:12:44.024Z",
  "title": "Chat",
  "inherits_status": true,
  "type": "Chat::Transcript",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3ODk4NT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--f745f0a5dc8108b7f361e578d47b72ff974ed50e.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069478985/subscription.json",
  "position": 4,
  "bucket": {
    "id": 2085958502,
    "name": "Honcho Design Newsroom",
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
    "created_at": "2026-03-23T22:12:24.947Z",
    "updated_at": "2026-03-23T22:12:26.266Z",
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
  "lines_url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985/lines.json",
  "files_url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985/uploads.json"
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
    "id": 1069479068,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2025-12-28T04:45:00.000Z",
    "updated_at": "2025-12-28T04:45:00.000Z",
    "title": "I'm hungry",
    "inherits_status": true,
    "type": "Chat::Lines::RichText",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985/lines/1069479068.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985@1069479068",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTA2OD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--ed75de023587361ebed66cce122997d56faeaa2e.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479068/boosts.json",
    "parent": {
      "id": 1069478985,
      "title": "Chat",
      "type": "Chat::Transcript",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985"
    },
    "bucket": {
      "id": 2085958502,
      "name": "Honcho Design Newsroom",
      "type": "Project"
    },
    "creator": {
      "id": 1049715929,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkyOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--d79103e78a10cd9f8ecda7470ea315674ac8a79a",
      "name": "Matt Donahue",
      "email_address": "matt@honchodesign.com",
      "personable_type": "User",
      "title": "Global Data Strategist",
      "bio": null,
      "location": null,
      "created_at": "2026-03-23T22:12:31.453Z",
      "updated_at": "2026-03-23T22:12:31.453Z",
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNlkkT4=--0f3c77d8c13069d514fd3f0ad694a67e426bad0f/avatar",
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    },
    "content": "I'm hungry"
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
  "id": 1069479054,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2025-12-27T21:34:00.000Z",
  "updated_at": "2025-12-27T21:34:00.000Z",
  "title": "👏 🎉",
  "inherits_status": true,
  "type": "Chat::Lines::RichText",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985/lines/1069479054.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985@1069479054",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTA1ND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--bf7b55e226a9c3111e0a8639faa1012b4db18bb1.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479054/boosts.json",
  "parent": {
    "id": 1069478985,
    "title": "Chat",
    "type": "Chat::Transcript",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985"
  },
  "bucket": {
    "id": 2085958502,
    "name": "Honcho Design Newsroom",
    "type": "Project"
  },
  "creator": {
    "id": 1049715915,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--56bb1f99675fd8fe08f93a706a5d2ddaa8412625",
    "name": "Amy Rivera",
    "email_address": "amy@honchodesign.com",
    "personable_type": "User",
    "title": "Central Web Coordinator",
    "bio": "I never said most of the things I said",
    "location": null,
    "created_at": "2026-03-23T22:12:26.589Z",
    "updated_at": "2026-03-23T22:12:26.589Z",
    "admin": false,
    "owner": false,
    "client": false,
    "employee": false,
    "time_zone": "America/Chicago",
    "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMtkkT4=--9927c47a4cbee30a7f9aea667882496aba799149/avatar",
    "can_ping": true,
    "can_manage_projects": true,
    "can_manage_people": true,
    "can_access_timesheet": true,
    "can_access_hill_charts": true
  },
  "content": "👏 🎉"
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
  "id": 1069479921,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-03-23T22:24:02.130Z",
  "updated_at": "2026-03-23T22:24:02.130Z",
  "title": "Good morning",
  "inherits_status": true,
  "type": "Chat::Lines::Text",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985/lines/1069479921.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985@1069479921",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTkyMT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--6ade20edbced6251605aa6d0c71c19fac57013e8.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479921/boosts.json",
  "parent": {
    "id": 1069478985,
    "title": "Chat",
    "type": "Chat::Transcript",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985"
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
    "email_address": "victor@honchodesign.com",
    "personable_type": "User",
    "title": "Chief Strategist",
    "bio": "Don’t let your dreams be dreams",
    "location": "Chicago, IL",
    "created_at": "2026-03-23T22:12:24.947Z",
    "updated_at": "2026-03-23T22:12:26.266Z",
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
  "id": 1069479922,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-03-23T22:24:02.742Z",
  "updated_at": "2026-03-23T22:24:02.742Z",
  "title": "Hello from the API",
  "inherits_status": true,
  "type": "Chat::Lines::RichText",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985/lines/1069479922.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985@1069479922",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTkyMj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--2f79012f8bcea232dbe72d1e81c267a5600198da.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479922/boosts.json",
  "parent": {
    "id": 1069478985,
    "title": "Chat",
    "type": "Chat::Transcript",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985"
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
    "email_address": "victor@honchodesign.com",
    "personable_type": "User",
    "title": "Chief Strategist",
    "bio": "Don’t let your dreams be dreams",
    "location": "Chicago, IL",
    "created_at": "2026-03-23T22:12:24.947Z",
    "updated_at": "2026-03-23T22:12:26.266Z",
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
    "id": 1069479923,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-03-23T22:24:03.474Z",
    "updated_at": "2026-03-23T22:24:03.508Z",
    "title": "company-logo.png",
    "inherits_status": true,
    "type": "Chat::Lines::Upload",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985/lines/1069479923.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985@1069479923",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTkyMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--26d3e497fe5ffd348020059b27de003e83af600b.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479923/boosts.json",
    "parent": {
      "id": 1069478985,
      "title": "Chat",
      "type": "Chat::Transcript",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985"
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
      "email_address": "victor@honchodesign.com",
      "personable_type": "User",
      "title": "Chief Strategist",
      "bio": "Don’t let your dreams be dreams",
      "location": "Chicago, IL",
      "created_at": "2026-03-23T22:12:24.947Z",
      "updated_at": "2026-03-23T22:12:26.266Z",
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
        "url": "https://3.basecampapi.com/195539477/blobs/79bd8420c4583af1392fa6e11775cabbf0dfcc82/previews/full",
        "filename": "company-logo.png",
        "content_type": "image/png",
        "byte_size": 1281,
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/79bd8420c4583af1392fa6e11775cabbf0dfcc82/download/company-logo.png"
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
  "id": 1069479923,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-03-23T22:24:03.474Z",
  "updated_at": "2026-03-23T22:24:03.508Z",
  "title": "company-logo.png",
  "inherits_status": true,
  "type": "Chat::Lines::Upload",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985/lines/1069479923.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985@1069479923",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTkyMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--26d3e497fe5ffd348020059b27de003e83af600b.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479923/boosts.json",
  "parent": {
    "id": 1069478985,
    "title": "Chat",
    "type": "Chat::Transcript",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478985.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478985"
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
    "email_address": "victor@honchodesign.com",
    "personable_type": "User",
    "title": "Chief Strategist",
    "bio": "Don’t let your dreams be dreams",
    "location": "Chicago, IL",
    "created_at": "2026-03-23T22:12:24.947Z",
    "updated_at": "2026-03-23T22:12:26.266Z",
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
      "url": "https://3.basecampapi.com/195539477/blobs/79bd8420c4583af1392fa6e11775cabbf0dfcc82/previews/full",
      "filename": "company-logo.png",
      "content_type": "image/png",
      "byte_size": 1281,
      "download_url": "https://storage.3.basecamp.com/195539477/blobs/79bd8420c4583af1392fa6e11775cabbf0dfcc82/download/company-logo.png"
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
