Events
======

An event is created any time a [recording][recordings] changes.

Endpoints:

- [Get events](#get-events)

Get events
----------

* `GET /recordings/2/events.json` will return a [paginated list][pagination] of events for the recording with an ID of `2`.

###### Example JSON Response
<!-- START GET /recordings/2/events.json -->
```json
[
  {
    "id": 1052474017,
    "recording_id": 1069480015,
    "action": "uncompleted",
    "details": {},
    "created_at": "2026-07-21T01:06:20.752Z",
    "creator": {
      "id": 1049715930,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzMD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--322099b137f9e0b6bc944b5b9fe7a2692da94814",
      "name": "Sharon Bradford",
      "personable_type": "User",
      "title": "Principal Branding Administrator",
      "tagline": null,
      "location": null,
      "created_at": "2026-05-28T17:22:28.137Z",
      "updated_at": "2026-05-28T17:22:28.137Z",
      "email_address": "sharon@honchodesign.com",
      "bio": null,
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNpkkT4=--789594e5e542ab99e467a51c9dec0a9035abc0e0/avatar",
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    }
  },
  {
    "id": 1052474016,
    "recording_id": 1069480015,
    "action": "completed",
    "details": {
      "notified_recipient_ids": [
        1049715938
      ]
    },
    "created_at": "2026-07-21T01:06:20.129Z",
    "creator": {
      "id": 1049715930,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzMD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--322099b137f9e0b6bc944b5b9fe7a2692da94814",
      "name": "Sharon Bradford",
      "personable_type": "User",
      "title": "Principal Branding Administrator",
      "tagline": null,
      "location": null,
      "created_at": "2026-05-28T17:22:28.137Z",
      "updated_at": "2026-05-28T17:22:28.137Z",
      "email_address": "sharon@honchodesign.com",
      "bio": null,
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNpkkT4=--789594e5e542ab99e467a51c9dec0a9035abc0e0/avatar",
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    },
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480015/events/1052474016/boosts.json"
  },
  {
    "id": 1052473949,
    "recording_id": 1069480015,
    "action": "uncompleted",
    "details": {},
    "created_at": "2026-07-21T00:06:16.458Z",
    "creator": {
      "id": 1049715930,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzMD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--322099b137f9e0b6bc944b5b9fe7a2692da94814",
      "name": "Sharon Bradford",
      "personable_type": "User",
      "title": "Principal Branding Administrator",
      "tagline": null,
      "location": null,
      "created_at": "2026-05-28T17:22:28.137Z",
      "updated_at": "2026-05-28T17:22:28.137Z",
      "email_address": "sharon@honchodesign.com",
      "bio": null,
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNpkkT4=--789594e5e542ab99e467a51c9dec0a9035abc0e0/avatar",
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    }
  },
  {
    "id": 1052473948,
    "recording_id": 1069480015,
    "action": "completed",
    "details": {
      "notified_recipient_ids": [
        1049715938
      ]
    },
    "created_at": "2026-07-21T00:06:15.563Z",
    "creator": {
      "id": 1049715930,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzMD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--322099b137f9e0b6bc944b5b9fe7a2692da94814",
      "name": "Sharon Bradford",
      "personable_type": "User",
      "title": "Principal Branding Administrator",
      "tagline": null,
      "location": null,
      "created_at": "2026-05-28T17:22:28.137Z",
      "updated_at": "2026-05-28T17:22:28.137Z",
      "email_address": "sharon@honchodesign.com",
      "bio": null,
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNpkkT4=--789594e5e542ab99e467a51c9dec0a9035abc0e0/avatar",
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    },
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480015/events/1052473948/boosts.json"
  },
  {
    "id": 1052473881,
    "recording_id": 1069480015,
    "action": "uncompleted",
    "details": {},
    "created_at": "2026-07-21T00:01:49.884Z",
    "creator": {
      "id": 1049715930,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzMD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--322099b137f9e0b6bc944b5b9fe7a2692da94814",
      "name": "Sharon Bradford",
      "personable_type": "User",
      "title": "Principal Branding Administrator",
      "tagline": null,
      "location": null,
      "created_at": "2026-05-28T17:22:28.137Z",
      "updated_at": "2026-05-28T17:22:28.137Z",
      "email_address": "sharon@honchodesign.com",
      "bio": null,
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNpkkT4=--789594e5e542ab99e467a51c9dec0a9035abc0e0/avatar",
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    }
  },
  {
    "id": 1052473880,
    "recording_id": 1069480015,
    "action": "completed",
    "details": {
      "notified_recipient_ids": [
        1049715938
      ]
    },
    "created_at": "2026-07-21T00:01:48.794Z",
    "creator": {
      "id": 1049715930,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzMD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--322099b137f9e0b6bc944b5b9fe7a2692da94814",
      "name": "Sharon Bradford",
      "personable_type": "User",
      "title": "Principal Branding Administrator",
      "tagline": null,
      "location": null,
      "created_at": "2026-05-28T17:22:28.137Z",
      "updated_at": "2026-05-28T17:22:28.137Z",
      "email_address": "sharon@honchodesign.com",
      "bio": null,
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNpkkT4=--789594e5e542ab99e467a51c9dec0a9035abc0e0/avatar",
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    },
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480015/events/1052473880/boosts.json"
  },
  {
    "id": 1052473437,
    "recording_id": 1069480015,
    "action": "assignment_changed",
    "details": {
      "added_person_ids": [
        1049715930
      ],
      "removed_person_ids": []
    },
    "created_at": "2026-05-12T05:24:00.000Z",
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
    }
  },
  {
    "id": 1052473436,
    "recording_id": 1069480015,
    "action": "created",
    "details": {
      "notified_recipient_ids": []
    },
    "created_at": "2026-05-12T05:24:00.000Z",
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
    }
  }
]
```
<!-- END GET /recordings/2/events.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/events.json
```

Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/recordings/2/events.json` → [Get events](#get-events)

[recordings]: recordings.md#recordings
[pagination]: ../README.md#pagination
