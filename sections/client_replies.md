Client replies
==============

Client replies are nested under the recording ID of a [client correspondence][correspondences] or [client approval][approvals].

Endpoints:

- [Get client replies](#get-client-replies)
- [Get a client reply](#get-a-client-reply)

Get client replies
------------------

* `GET /buckets/1/client/recordings/2/replies.json` will return a [paginated list][pagination] of client replies for the recording with ID `2`.

###### Example JSON Response
<!-- START GET /buckets/1/client/recordings/2/replies.json -->
```json
[
  {
    "id": 1069480062,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-04-14T22:55:00.000Z",
    "updated_at": "2026-04-14T22:55:00.000Z",
    "title": "Re: Project kickoff!",
    "inherits_status": true,
    "type": "Client::Reply",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/replies/1069480062.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/client/correspondences/1069480061#__recording_1069480062",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDA2Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--7c826d155ead13d260733b9507c9e92c070d7579.json",
    "parent": {
      "id": 1069480061,
      "title": "Project kickoff!",
      "type": "Client::Correspondence",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/correspondences/1069480061.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/client/correspondences/1069480061"
    },
    "bucket": {
      "id": 2085958506,
      "name": "The Leto Locator",
      "type": "Project"
    },
    "creator": {
      "id": 1049715935,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--d8bb591232517f997e82d5a8f68e4c9c9033e60f",
      "name": "Stephen Early",
      "personable_type": "Client",
      "title": "National Directives Director",
      "tagline": null,
      "location": null,
      "created_at": "2026-05-28T17:22:29.134Z",
      "updated_at": "2026-05-28T17:22:29.134Z",
      "email_address": "stephen@letobrand.com",
      "bio": null,
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "Etc/UTC",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBN9kkT4=--7df21243a6650f691505323b707250c92aeb468d/avatar",
      "company": {
        "id": 1033447818,
        "name": "Leto Brand"
      },
      "can_ping": true,
      "can_manage_projects": false,
      "can_manage_people": false,
      "can_access_timesheet": false,
      "can_access_hill_charts": false
    },
    "content": "Hi all - we're excited to get started too.",
    "content_attachments": []
  }
]
```
<!-- END GET /buckets/1/client/recordings/2/replies.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/client/recordings/2/replies.json
```

Get a client reply
------------------

* `GET /buckets/1/client/recordings/2/replies/3.json` will return the client reply with an ID of `3` for the recording with an ID of `2`.

###### Example JSON Response
<!-- START GET /buckets/1/client/recordings/2/replies/3.json -->
```json
{
  "id": 1069480067,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-04-15T00:38:00.000Z",
  "updated_at": "2026-04-15T00:38:00.000Z",
  "title": "Re: Project kickoff!",
  "inherits_status": true,
  "type": "Client::Reply",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/replies/1069480067.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/client/correspondences/1069480061#__recording_1069480067",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDA2Nz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--cfdf6bea75c7b8db779f6832f6d260dfba6d5165.json",
  "parent": {
    "id": 1069480061,
    "title": "Project kickoff!",
    "type": "Client::Correspondence",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/correspondences/1069480061.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/client/correspondences/1069480061"
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
  "content": "Hi Leto team, this is Annie. I'll be your day to day contact for the project, so keep me on your speed dial (or speed email, perhaps more accurately!) Feel free to reach out to me with any questions at all, and I'll be posting up some outlines, timelines, etc. very shortly.",
  "content_attachments": []
}
```
<!-- END GET /buckets/1/client/recordings/2/replies/3.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/client/recordings/2/replies/3.json
```


[pagination]: ../README.md#pagination
[correspondences]: client_correspondences.md#client-correspondences
[approvals]: client_approvals.md#client-approvals
