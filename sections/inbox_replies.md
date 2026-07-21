Inbox replies
==============

Inbox replies are nested under the recording ID of a [forward][forwards].

Endpoints:

- [Get inbox replies](#get-inbox-replies)
- [Get an inbox reply](#get-an-inbox-reply)

Get inbox replies
-------------------

* `GET /inbox_forwards/2/replies.json` will return a [paginated list][pagination] of inbox replies for the forward with ID of `2`.

###### Example JSON Response
<!-- START GET /inbox_forwards/2/replies.json -->
```json
[
  {
    "id": 1069479460,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-03-09T20:50:00.000Z",
    "updated_at": "2026-03-09T20:50:00.000Z",
    "title": "Re: Can we make the logo pop?",
    "inherits_status": true,
    "type": "Inbox::Reply",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/inbox_replies/1069479460.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/inbox_forwards/1069479459#__recording_1069479460",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTQ2MD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--53766326b89a612f1d6c29abee9cc9d1453368ef.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479460/boosts.json",
    "parent": {
      "id": 1069479459,
      "title": "Can we make the logo pop?",
      "type": "Inbox::Forward",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958502/inbox_forwards/1069479459.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/inbox_forwards/1069479459"
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
    "content": "Hey Henry!<br><br>Thanks for the quick feedback re: the logo. I know what you mean about feeling \"flat,\" but I'm not quite sure a rainbow is the way to go. I'll ping the design team and see what they can come up with later today. We'll post designs here in Basecamp when they're ready!<br><br><br>--VC",
    "content_attachments": []
  }
]
```
<!-- END GET /inbox_forwards/2/replies.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/inbox_forwards/2/replies.json
```

Get an inbox reply
-------------------

* `GET /inbox_forwards/2/replies/3.json` will return the inbox reply with an ID of `3` for the forward with an ID of `2`.

###### Example JSON Response
<!-- START GET /inbox_forwards/2/replies/3.json -->
```json
{
  "id": 1069479463,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-03-09T21:52:00.000Z",
  "updated_at": "2026-03-09T21:52:00.000Z",
  "title": "Re: Can we make the logo pop?",
  "inherits_status": true,
  "type": "Inbox::Reply",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958502/inbox_replies/1069479463.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/inbox_forwards/1069479459#__recording_1069479463",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTQ2Mz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--7c330da1c850a64cb45319e0d9d84c101500bc5c.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479463/boosts.json",
  "parent": {
    "id": 1069479459,
    "title": "Can we make the logo pop?",
    "type": "Inbox::Forward",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/inbox_forwards/1069479459.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/inbox_forwards/1069479459"
  },
  "bucket": {
    "id": 2085958502,
    "name": "Honcho Design Newsroom",
    "type": "Project"
  },
  "creator": {
    "id": 1049715934,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--7d5db20d1c81088ab8e6377a3d5a9ce48a0e0966",
    "name": "henry@letobrand.com",
    "personable_type": "Outsider",
    "title": null,
    "tagline": null,
    "location": null,
    "created_at": "2026-05-28T17:22:29.119Z",
    "updated_at": "2026-05-28T17:22:29.119Z",
    "email_address": "henry@letobrand.com",
    "bio": null,
    "admin": false,
    "owner": false,
    "client": false,
    "employee": false,
    "time_zone": "Etc/UTC",
    "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBN5kkT4=--f1717e24836df2add6c33af21bd7b02493a0b95c/avatar",
    "can_ping": true,
    "can_manage_projects": false,
    "can_manage_people": false,
    "can_access_timesheet": false,
    "can_access_hill_charts": false
  },
  "content": "Awesome, sounds good Victor!<br><br>Thanks again,<br>Henry",
  "content_attachments": []
}
```
<!-- END GET /inbox_forwards/2/replies/3.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/inbox_forwards/2/replies/3.json
```

Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/inbox_forwards/2/replies.json` → [Get inbox replies](#get-inbox-replies)
* `GET /buckets/1/inbox_forwards/2/replies/3.json` → [Get an inbox reply](#get-an-inbox-reply)

[pagination]: ../README.md#pagination
[forwards]: forwards.md#forwards
