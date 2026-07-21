Forwards
========

Endpoints:

- [Get forwards](#get-forwards)
- [Get a forward](#get-a-forward)
- [Trash a forward][1]


Get forwards
------------

* `GET /inboxes/3/inbox_forwards.json` will return a [paginated list][2] of active forwards in the inbox with an ID of `3`.

To get the inbox ID for a project, see the [Get inbox][3] endpoint.

_Optional query parameters_:

* `sort` - Options: `created_at` or `updated_at`. Default: `created_at`.
* `direction` - Options: `desc` or `asc`. Default: `desc`.

###### Example JSON Response
<!-- START GET /inboxes/3/inbox_forwards.json -->
```json
[
  {
    "id": 1069479459,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-05-28T17:22:56.122Z",
    "updated_at": "2026-05-28T17:22:56.248Z",
    "title": "Can we make the logo pop?",
    "inherits_status": true,
    "type": "Inbox::Forward",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/inbox_forwards/1069479459.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/inbox_forwards/1069479459",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTQ1OT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--4d80cddb3e8f4e4370eb6be40a16915daff17966.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479459/subscription.json",
    "parent": {
      "id": 1069478966,
      "title": "Email Forwards",
      "type": "Inbox",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958502/inboxes/1069478966.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/inboxes/1069478966"
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
    "content": "---------- Forwarded message ---------- From: \"Henry Bowman\"  Date: Oct 15, 2013 1:13 AM Subject: Can we make the logo pop? To: \"Victor Cooper\"  Hey Victor, I know it's late at night, but I had a quick thought about the logo. It feels, I dunno, flat. Is there anything you could do to make it pop? I'm thinking it needs more sizzle. More... SOMETHING. Maybe we could try adding a rainbow? Let's take a look mid-day tomorrow and re-group with the rest of the team. Cheers, Henry",
    "content_attachments": [],
    "subject": "Can we make the logo pop?",
    "from": null,
    "replies_count": 2,
    "replies_url": "https://3.basecampapi.com/195539477/buckets/2085958502/inbox_forwards/1069479459/replies.json"
  }
]
```
<!-- END GET /inboxes/3/inbox_forwards.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/inboxes/3/inbox_forwards.json
```


Get a forward
-------------

* `GET /inbox_forwards/2.json` will return the forward with an ID of `2`.

###### Example JSON Response
<!-- START GET /inbox_forwards/2.json -->
```json
{
  "id": 1069479458,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-28T17:22:56.039Z",
  "updated_at": "2026-05-28T17:22:56.045Z",
  "title": "Some technical details",
  "inherits_status": true,
  "type": "Inbox::Forward",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958502/inbox_forwards/1069479458.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/inbox_forwards/1069479458",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTQ1OD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--7bbc0b742667aba54640eba3fab6a979f555d5e1.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479458/subscription.json",
  "parent": {
    "id": 1069478966,
    "title": "Email Forwards",
    "type": "Inbox",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/inboxes/1069478966.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/inboxes/1069478966"
  },
  "bucket": {
    "id": 2085958502,
    "name": "Honcho Design Newsroom",
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
  "content": "---------- Forwarded message ---------- From: \"Beth Allen\"  Date: Oct 13, 2013 1:38 PM Subject: Some technical details To: \"Annie Bryan\"  Hey Team Honcho, Just wanted to let you know I'm a big fan of your blog. Your writing is so inspiring. Thanks for sharing!",
  "content_attachments": [],
  "subject": "Some technical details",
  "from": null,
  "replies_count": 0,
  "replies_url": "https://3.basecampapi.com/195539477/buckets/2085958502/inbox_forwards/1069479458/replies.json"
}
```
<!-- END GET /inbox_forwards/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/inbox_forwards/2.json
```

Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/inboxes/3/inbox_forwards.json` → [Get forwards](#get-forwards)
* `GET /buckets/1/inbox_forwards/2.json` → [Get a forward](#get-a-forward)

[1]: recordings.md#trash-a-recording
[2]: ../README.md#pagination
[3]: inboxes.md#inboxes
