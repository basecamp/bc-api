Client correspondences
======================

Endpoints:

- [Get client correspondences](#get-client-correspondences)
- [Get a client correspondence](#get-a-client-correspondence)

Get client correspondences
--------------------------

* `GET /buckets/1/client/correspondences.json` will return a [paginated list][pagination] of client correspondences in the project with an ID of `1`.

_Optional query parameters_:

* `sort` - Options: `created_at` or `updated_at`. Default: `created_at`.
* `direction` - Options: `desc` or `asc`. Default: `desc`.

###### Example JSON Response
<!-- START GET /buckets/1/client/correspondences.json -->
```json
[
  {
    "id": 1069480141,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-05-23T18:49:00.000Z",
    "updated_at": "2026-05-28T17:23:35.277Z",
    "title": "Final deliverables and launch are right around the corner",
    "inherits_status": true,
    "type": "Client::Correspondence",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/correspondences/1069480141.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/client/correspondences/1069480141",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDE0MT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--b65ce3084226314664690e8f4d8a8992cf5c214d.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958506/recordings/1069480141/subscription.json",
    "parent": {
      "id": 1069480059,
      "title": "The Clientside",
      "type": "Client::Board",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/board.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/client/board"
    },
    "bucket": {
      "id": 2085958506,
      "name": "The Leto Locator",
      "type": "Project"
    },
    "creator": {
      "id": 1049715938,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--4ccc567a0a3b10e354bca909b704637b601f0b16",
      "name": "Annie Bryan",
      "personable_type": "User",
      "title": "Central Markets Manager",
      "tagline": "To open a store is easy, to keep it open is an art",
      "location": null,
      "created_at": "2026-05-28T17:22:29.167Z",
      "updated_at": "2026-05-28T17:22:29.167Z",
      "email_address": "annie@honchodesign.com",
      "bio": "To open a store is easy, to keep it open is an art",
      "admin": false,
      "owner": false,
      "client": false,
      "employee": true,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOJkkT4=--732a71fbd28ec10d9bf4466abd3588a8bea40bdb/avatar",
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
    "content": "",
    "content_attachments": [],
    "subject": "Final deliverables and launch are right around the corner",
    "replies_count": 5,
    "replies_url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/recordings/1069480141/replies.json"
  }
]
```
<!-- END GET /buckets/1/client/correspondences.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/client/correspondences.json
```

Get a client correspondence
---------------------------

* `GET /client/correspondences/2.json` will return the client correspondence with an ID of `2`.

###### Example JSON Response
<!-- START GET /client/correspondences/2.json -->
```json
{
  "id": 1069480061,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-04-14T21:59:00.000Z",
  "updated_at": "2026-05-28T17:23:30.499Z",
  "title": "Project kickoff!",
  "inherits_status": true,
  "type": "Client::Correspondence",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/correspondences/1069480061.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/client/correspondences/1069480061",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDA2MT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--b01fb0b9519ebf3b542fda2c036c46811927b99b.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958506/recordings/1069480061/subscription.json",
  "parent": {
    "id": 1069480059,
    "title": "The Clientside",
    "type": "Client::Board",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/board.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/client/board"
  },
  "bucket": {
    "id": 2085958506,
    "name": "The Leto Locator",
    "type": "Project"
  },
  "creator": {
    "id": 1049715922,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkyMj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--ed42dd1af36c4756554ffb2a20de4e019f0c28d3",
    "name": "Jay Edmonds",
    "personable_type": "User",
    "title": "Internal Marketing Assistant",
    "tagline": null,
    "location": null,
    "created_at": "2026-05-28T17:22:25.544Z",
    "updated_at": "2026-05-28T17:22:25.544Z",
    "email_address": "jay@honchodesign.com",
    "bio": null,
    "admin": false,
    "owner": false,
    "client": false,
    "employee": false,
    "time_zone": "America/Chicago",
    "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNJkkT4=--6ef93d58440c2ed1fec4457e3eb5f09572e866a4/avatar",
    "can_ping": true,
    "can_manage_projects": true,
    "can_manage_people": true,
    "can_access_timesheet": true,
    "can_access_hill_charts": true
  },
  "content": "",
  "content_attachments": [],
  "subject": "Project kickoff!",
  "replies_count": 6,
  "replies_url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/recordings/1069480061/replies.json"
}
```
<!-- END GET /client/correspondences/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/client/correspondences/2.json
```


Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/client/correspondences/2.json` → [Get a client correspondence](#get-a-client-correspondence)

[pagination]: ../README.md#pagination
