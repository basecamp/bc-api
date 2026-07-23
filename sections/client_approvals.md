Client approvals
================

Endpoints:

- [Get client approvals](#get-client-approvals)
- [Get a client approval](#get-a-client-approval)

Get client approvals
--------------------

* `GET /buckets/1/client/approvals.json` will return a [paginated list][pagination] of client approvals in the project with an ID of `1`.

_Optional query parameters_:

* `sort` - Options: `created_at` or `updated_at`. Default: `created_at`.
* `direction` - Options: `desc` or `asc`. Default: `desc`.

###### Example JSON Response
<!-- START GET /buckets/1/client/approvals.json -->
```json
[
  {
    "id": 1069480149,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-05-27T14:24:00.000Z",
    "updated_at": "2026-05-27T14:24:00.000Z",
    "title": "Business card",
    "inherits_status": true,
    "type": "Client::Approval",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/approvals/1069480149.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/client/approvals/1069480149",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDE0OT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--05df570edfdb3d2e4a29228e6ac0487064a429b2.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958506/recordings/1069480149/subscription.json",
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
    "subject": "Business card",
    "due_on": null,
    "replies_count": 0,
    "replies_url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/recordings/1069480149/replies.json",
    "approval_status": "pending",
    "approver": {
      "id": 1049715936,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzNj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--55b2520c141258726568f476e5bbceb75c25e774",
      "name": "Miranda Grant",
      "personable_type": "Client",
      "title": "Dynamic Markets Analyst",
      "tagline": null,
      "location": null,
      "created_at": "2026-05-28T17:22:29.141Z",
      "updated_at": "2026-05-28T17:22:29.141Z",
      "email_address": "miranda@letobrand.com",
      "bio": null,
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "Etc/UTC",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOBkkT4=--78fb2ba7c3091268f41638ef90dee7dd32f395d6/avatar",
      "company": {
        "id": 1033447818,
        "name": "Leto Brand"
      },
      "can_ping": true,
      "can_manage_projects": false,
      "can_manage_people": false,
      "can_access_timesheet": false,
      "can_access_hill_charts": false
    }
  }
]
```
<!-- END GET /buckets/1/client/approvals.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/client/approvals.json
```

Get a client approval
---------------------

* `GET /client/approvals/2.json` will return the client approval with an ID of `2`.

###### Example JSON Response
<!-- START GET /client/approvals/2.json -->
```json
{
  "id": 1069480147,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-24T16:12:00.000Z",
  "updated_at": "2026-05-28T17:23:35.399Z",
  "title": "New logo for the website",
  "inherits_status": true,
  "type": "Client::Approval",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/approvals/1069480147.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/client/approvals/1069480147",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDE0Nz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--7db68241afa0761e486b6c84454be5348fd793fa.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958506/recordings/1069480147/subscription.json",
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
  "subject": "New logo for the website",
  "due_on": null,
  "replies_count": 0,
  "replies_url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/recordings/1069480147/replies.json",
  "approval_status": "approved",
  "approver": {
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
  "responses": [
    {
      "id": 1069480148,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-05-24T16:45:00.000Z",
      "updated_at": "2026-05-24T16:45:00.000Z",
      "title": "Answer Re: New logo for the website",
      "inherits_status": true,
      "type": "Client::Approval::Response",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/client/approvals/1069480147#__recording_1069480148",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDE0OD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--d4490ebba40ac12d277b86b2a8862a41b1654cf9.json",
      "parent": {
        "id": 1069480147,
        "title": "New logo for the website",
        "type": "Client::Approval",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958506/client/approvals/1069480147.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958506/client/approvals/1069480147"
      },
      "bucket": {
        "id": 2085958506,
        "name": "The Leto Locator",
        "type": "Project"
      },
      "creator": {
        "id": 1049715937,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzNz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--86a39f74ccfe7d8d0a393a80b92182b9a85819d0",
        "name": "Beth Allen",
        "personable_type": "Client",
        "title": "Product Tactics Architect",
        "tagline": null,
        "location": null,
        "created_at": "2026-05-28T17:22:29.147Z",
        "updated_at": "2026-05-28T17:22:29.147Z",
        "email_address": "beth@letobrand.com",
        "bio": null,
        "admin": false,
        "owner": false,
        "client": false,
        "employee": false,
        "time_zone": "Etc/UTC",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOFkkT4=--560f7fa1330d4341e3c089226bcb7fefb82dbfd1/avatar",
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
      "content": "Looks great! Thanks for all your hard work on this.",
      "approved": true
    }
  ]
}
```
<!-- END GET /client/approvals/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/client/approvals/2.json
```


Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/client/approvals/2.json` → [Get a client approval](#get-a-client-approval)

[pagination]: ../README.md#pagination
