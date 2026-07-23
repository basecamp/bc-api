Google documents
=================

A [Google document][google_documents] is a [recording][recordings] type that links to a
Google Workspace document (Google Docs, Sheets, Slides, …) and lives inside a
[vault][vaults]. The `document_type` field is one of `doc`, `sheet`, `slide`, `other`.

Endpoints:

- [Get a Google document](#get-a-google-document)
- [Create a Google document](#create-a-google-document)
- [Update a Google document](#update-a-google-document)
- [Trash a Google document][trash]

[google_documents]: ../README.md#recordings-bucket-contents
[recordings]: recordings.md
[vaults]: vaults.md
[trash]: recordings.md#trash-a-recording

Get a Google document
---------------------

* `GET /google_documents/2.json` will return the [Google document][google_documents] with
  an ID of `2`.

###### Example JSON Response
<!-- START GET /google_documents/2.json -->
```json
{
  "id": 1069480366,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-07-21T00:02:33.316Z",
  "updated_at": "2026-07-21T00:02:33.388Z",
  "title": "Roadmap (draft)",
  "inherits_status": true,
  "type": "GoogleDocument",
  "url": "https://docs.google.com/document/d/abcd1234/edit",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/google_documents/1069480366",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDM2Nj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--8ab1d5cc9f9224b76af3853b0365bc5f1a42e4a5.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480366/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480366/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480366/boosts.json",
  "position": 1,
  "parent": {
    "id": 1069479830,
    "title": "Docs & Files",
    "type": "Vault",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/vaults/1069479830.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/vaults/1069479830"
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
  "description": "<div dir=\"auto\">Quarterly roadmap document</div>",
  "description_attachments": [],
  "document_type": "doc"
}
```
<!-- END GET /google_documents/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/google_documents/2.json
```

Create a Google document
------------------------

* `POST /buckets/1/vaults/3/google_documents.json` will create a new Google document under
  the [vault][vaults] with ID `3` in the [project][projects] with ID `1`.

###### Required parameters

| Param        | Type   | Description |
| ------------ | ------ | ----------- |
| `url`        | String | The URL of the Google Workspace document. |
| `document_type` | String | One of `doc`, `sheet`, `slide`, `other`. |

###### Optional parameters

| Param         | Type    | Description |
| ------------- | ------- | ----------- |
| `title`       | String | The document's title. Defaults to `Untitled` when omitted. |
| `description` | HTML    | Rich-text description. |
| `status`      | String  | `active` to publish immediately, `drafted` to keep as a draft. Defaults to `drafted`. |
| `subscriptions` | Array<Integer> | IDs of [people][people] to subscribe to comments and boosts. |
| `visible_to_clients` | Boolean | A **top-level** field — a sibling of the `google_document` object, *not* inside it. When the project has clients enabled, whether the document is visible to them. Defaults to `false`; a **client** caller always creates client-visible records. Applies only when creating directly in the tool's vault; items created inside a folder inherit the folder's visibility. See [Client visibility][client_visibility]. |

[projects]: projects.md
[people]: people.md
[client_visibility]: client_visibility.md

###### Example JSON Request
<!-- START POST PAYLOAD /buckets/1/vaults/3/google_documents.json -->
```json
{
  "google_document": {
    "title": "Roadmap",
    "description": "<div>Quarterly roadmap document</div>",
    "url": "https://docs.google.com/document/d/abcd1234/edit",
    "document_type": "doc"
  },
  "visible_to_clients": true
}
```
<!-- END POST PAYLOAD /buckets/1/vaults/3/google_documents.json -->

A successful create returns `201 Created` with the new Google document's JSON shape:

###### Example JSON Response
<!-- START POST /buckets/1/vaults/3/google_documents.json -->
```json
{
  "id": 1069480443,
  "status": "drafted",
  "visible_to_clients": true,
  "created_at": "2026-07-21T01:06:50.879Z",
  "updated_at": "2026-07-21T01:06:50.896Z",
  "title": "Roadmap",
  "inherits_status": false,
  "type": "GoogleDocument",
  "url": "https://docs.google.com/document/d/abcd1234/edit",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/google_documents/1069480443",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDQ0Mz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--243e46e38cc2055cbdf56e960011bb4c7bc29bcf.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480443/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480443/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480443/boosts.json",
  "parent": {
    "id": 1069479830,
    "title": "Docs & Files",
    "type": "Vault",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/vaults/1069479830.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/vaults/1069479830"
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
  "description": "<div dir=\"auto\">Quarterly roadmap document</div>",
  "description_attachments": [],
  "document_type": "doc"
}
```
<!-- END POST /buckets/1/vaults/3/google_documents.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"google_document":{"title":"Roadmap","description":"<div>Quarterly roadmap document</div>","url":"https://docs.google.com/document/d/abcd1234/edit","document_type":"doc"}}' \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/vaults/3/google_documents.json
```

Update a Google document
------------------------

* `PUT /google_documents/2.json` will update the [Google document][google_documents]
  with an ID of `2`. The legacy bucket-scoped path
  `PUT /buckets/1/google_documents/2.json` is also accepted.

Update accepts `title`, `url`, `document_type`, and `description`, and all four are
sent on every update — the controller replaces the recordable on each call rather than
patching individual fields. `status` is also accepted; updating a drafted document
applies any `subscriptions` sent with the request.

###### Example JSON Request
<!-- START PUT PAYLOAD /buckets/1/google_documents/2.json -->
```json
{
  "google_document": {
    "title": "Roadmap (revised)",
    "description": "<div>Quarterly roadmap with revised scope</div>",
    "url": "https://docs.google.com/document/d/abcd1234/edit",
    "document_type": "doc"
  }
}
```
<!-- END PUT PAYLOAD /buckets/1/google_documents/2.json -->

Returns `200 OK` with the updated Google document's JSON shape:

###### Example JSON Response
<!-- START PUT /buckets/1/google_documents/2.json -->
```json
{
  "id": 1069480443,
  "status": "drafted",
  "visible_to_clients": true,
  "created_at": "2026-07-21T01:06:50.879Z",
  "updated_at": "2026-07-21T01:06:51.456Z",
  "title": "Roadmap (revised)",
  "inherits_status": false,
  "type": "GoogleDocument",
  "url": "https://docs.google.com/document/d/abcd1234/edit",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/google_documents/1069480443",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDQ0Mz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--243e46e38cc2055cbdf56e960011bb4c7bc29bcf.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480443/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480443/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480443/boosts.json",
  "parent": {
    "id": 1069479830,
    "title": "Docs & Files",
    "type": "Vault",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/vaults/1069479830.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/vaults/1069479830"
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
  "description": "<div dir=\"auto\">Quarterly roadmap with revised scope</div>",
  "description_attachments": [],
  "document_type": "doc"
}
```
<!-- END PUT /buckets/1/google_documents/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"google_document":{"title":"Roadmap (revised)","description":"<div>Quarterly roadmap with revised scope</div>","url":"https://docs.google.com/document/d/abcd1234/edit","document_type":"doc"}}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/google_documents/2.json
```
