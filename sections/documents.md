Documents
=========

Endpoints:

- [Get documents](#get-documents)
- [Get a document](#get-a-document)
- [Create a document](#create-a-document)
- [Update a document](#update-a-document)
- [Trash a document][trash]

Get documents
-------------

* `GET /vaults/2/documents.json` will return a [paginated list][pagination] of active documents in the [vault][vaults] with ID of `2`.

###### Example JSON Response
<!-- START GET /vaults/2/documents.json -->
```json
[
  {
    "id": 1069479521,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-04-19T05:57:00.000Z",
    "updated_at": "2026-05-28T17:23:52.982Z",
    "title": "New Hire Info, Benefits Summary, and Forms",
    "inherits_status": true,
    "type": "Document",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/documents/1069479521.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/documents/1069479521",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTUyMT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--e32185484173314aa165d02f85f18e03515892b1.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479521/subscription.json",
    "comments_count": 1,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479521/comments.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479521/boosts.json",
    "position": 1,
    "parent": {
      "id": 1069479520,
      "title": "HR Stuff",
      "type": "Vault",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958502/vaults/1069479520.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/vaults/1069479520"
    },
    "bucket": {
      "id": 2085958502,
      "name": "Honcho Design Newsroom",
      "type": "Project"
    },
    "creator": {
      "id": 1049715939,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--91bd4d39e2f4af1d814a0b480e809d15a51df239",
      "name": "Cheryl Walters",
      "personable_type": "User",
      "title": "Corporate Integration Director",
      "tagline": "A joke is a very serious thing",
      "location": null,
      "created_at": "2026-05-28T17:22:29.505Z",
      "updated_at": "2026-05-28T17:22:29.505Z",
      "email_address": "cheryl@honchodesign.com",
      "bio": "A joke is a very serious thing",
      "admin": false,
      "owner": false,
      "client": false,
      "employee": true,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBONkkT4=--b57b5a44335d4c3ba1a2585abd6e5c7e4c85fdd6/avatar",
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
    "content": "<strong>Health Insurance</strong>\nWe have just one health insurance policy. The company pays most of the premium, and you cover the rest. Domestic partnerships are covered, as well as marriages. Open enrollment starts in January.<br><br>\n\n<strong>401K Retirement Plan</strong>\nWe match dollar-for-dollar up to 10% of your salary that you contribute to the plan. You are eligible to enroll in the 401K plan after your first paycheck.<br><br>\n\n<strong>Flexible Spending Account (FSA)</strong>\nThe FSA is an account where you can set aside pre-tax money for out-of-pocket medical expenses, such as prescriptions, OTC medicine, vision care, etc.  You have to decide up front how much money you want to put in the account, and the max is $2500/year.<br><br>\n\n<strong>Continuing Education Allowance</strong>\nWe provide you with $500 a year to take classes that help you professionally. Really, anything that helps you with your job.<br><br>\n\n<strong>Matching Charitable Gifts</strong>\nWhen you donate money to a qualified charity, we will make a matching gift to that charity on your behalf. The maximum for the year is $500 per employee.<br><br>\n\n<strong>Paid Time Off</strong>\nPaid time off doesn't really exist here - if you need a day (or week!) off, you just need to clear it with your team or others who would be affected by your absence. You should try to take at least 3 weeks off a year.",
    "content_attachments": []
  }
]
```
<!-- END GET /vaults/2/documents.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/vaults/2/documents.json
```

Get a document
--------------

* `GET /documents/2.json` will return the document with an ID of `2`.

###### Example JSON Response
<!-- START GET /documents/2.json -->
```json
{
  "id": 1069480277,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-25T12:05:00.000Z",
  "updated_at": "2026-05-25T12:05:00.000Z",
  "title": "Intro/Outro for Victor’s Interview",
  "inherits_status": true,
  "type": "Document",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958508/documents/1069480277.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958508/documents/1069480277",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI3Nz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--3fcb0a8baaa79a4e861eea6063ee2d79f05da1c0.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958508/recordings/1069480277/subscription.json",
  "comments_count": 1,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958508/recordings/1069480277/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958508/recordings/1069480277/boosts.json",
  "position": 2,
  "parent": {
    "id": 1069480172,
    "title": "Docs & Files",
    "type": "Vault",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958508/vaults/1069480172.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958508/vaults/1069480172"
  },
  "bucket": {
    "id": 2085958508,
    "name": "Making a Podcast",
    "type": "Project"
  },
  "creator": {
    "id": 1049715947,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk0Nz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--870648aaabd372d74612fbfe66aea6eb0f9fbd51",
    "name": "Cheryl Walters",
    "personable_type": "DummyUser",
    "title": null,
    "tagline": null,
    "location": null,
    "created_at": "2026-05-28T17:23:36.161Z",
    "updated_at": "2026-05-28T17:23:36.161Z",
    "email_address": null,
    "bio": null,
    "admin": false,
    "owner": false,
    "client": false,
    "employee": false,
    "time_zone": "America/Chicago",
    "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOtkkT4=--7b4adc39768c41c4f22a373c9fcd137f17b35b07/avatar",
    "can_ping": true,
    "can_manage_projects": false,
    "can_manage_people": false,
    "can_access_timesheet": false,
    "can_access_hill_charts": false
  },
  "content": "Welcome to this special bonus episode of REWORK, a podcast about a better way to work and run your business. REWORK be back next week with another regular episode. For today's special edition, I interviewed the founders of 37signals to dig deeper into remote work.<br><br>                 Thanks for listening to REWORK. We’ll be back next week with another regular episode! We’d love to hear what you think of the show. You can find show                 notes and transcripts at <a target=\"_blank\" rel=\"noreferrer\" class=\"autolinked\" data-behavior=\"truncate\" href=\"https://37signals.com/podcast/\">https://37signals.com/podcast/</a>. And as always REWORK is brought to you by 37signals, makers of Basecamp and HEY.",
  "content_attachments": []
}
```
<!-- END GET /documents/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/documents/2.json
```

Create a document
-----------------

* `POST /vaults/2/documents.json` creates a document under the vault with an ID of `2`.

**Required parameters**: `title` as the title of the document, and `content` as the body of the document. See our [Rich text guide][rich] for what HTML tags are allowed.

_Optional parameters_:

* `status` — set to `active` to publish the document immediately. **When `status` is omitted the document is created as a draft** (it defaults to `drafted`); a draft is not posted and notifies no one until you publish it. See [Publishing a draft](#publishing-a-draft).
* `visible_to_clients` - top-level boolean. When the project has clients enabled, whether the document is visible to them. Defaults to `false` (team callers creating directly under the docked tool); a **client** caller always creates client-visible records. Applies only when creating directly in the tool's vault; items created inside a folder inherit the folder's visibility. See [Client visibility][client_visibility] to change it after creation.

This endpoint will return `201 Created` with the current JSON representation of the document if the creation was a success. See the [Get a document](#get-a-document) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "title": "New Hire Info",
  "content": "<div><strong>Getting started</strong></div>",
  "status": "active"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"title":"New Hire Info","content":"<div><strong>Getting started</strong></div>","status":"active"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/vaults/2/documents.json
```

Update a document
-----------------

* `PUT /documents/2.json` allows changing the title and content of the document with an ID of `2`.

This endpoint will return `200 OK` with the current JSON representation of the document if the update was a success. See the [Get a document](#get-a-document) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "title": "New Hire Information",
  "content": "<div><strong>Let's get started</strong></div>"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"title":"New Hire Information","content":"<div><strong>Let's get started</strong></div>"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/documents/2.json
```

Publishing a draft
------------------

Publish a [draft](drafts.md) document by updating it with `status` set to `active`. Unlike a message, a document update **replaces** the document rather than merging, so you must resend `title` and `content` alongside `status`:

```json
{
  "title": "New Hire Info",
  "content": "<div><strong>Getting started</strong></div>",
  "status": "active"
}
```

A status-only update fails with `400 Bad Request` (the `document` parameters are required), and omitting a field clears its value. Publishing posts the document and notifies its subscribers exactly once — the same publication side-effects as [publishing a message](messages.md#publishing-a-draft).


Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/vaults/2/documents.json` → [Get documents](#get-documents)
* `GET /buckets/1/documents/2.json` → [Get a document](#get-a-document)
* `POST /buckets/1/vaults/2/documents.json` → [Create a document](#create-a-document)
* `PUT /buckets/1/documents/2.json` → [Update a document](#update-a-document)

[pagination]: ../README.md#pagination
[trash]: recordings.md#trash-a-recording
[vaults]: vaults.md#vaults
[rich]: rich_text.md
[client_visibility]: client_visibility.md
