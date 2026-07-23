Cloud files
===========

A [cloud file][cloud_files] is a [recording][recordings] type that links to a file or
document hosted on an external service (Dropbox, Google Drive, Figma, Notion, …) and
lives inside a [vault][vaults]. The service is identified by a string code (e.g.
`dropbox`, `google_doc`, `figma`); the response embeds the matching service struct so
clients can render the service name, supporting text, and example URL without a hard-coded
catalogue.

Endpoints:

- [Get a cloud file](#get-a-cloud-file)
- [Create a cloud file](#create-a-cloud-file)
- [Update a cloud file](#update-a-cloud-file)
- [Trash a cloud file][trash]

[cloud_files]: ../README.md#recordings-bucket-contents
[recordings]: recordings.md
[vaults]: vaults.md
[trash]: recordings.md#trash-a-recording

Get a cloud file
----------------

* `GET /cloud_files/2.json` will return the [cloud file][cloud_files] with an ID of `2`.

###### Example JSON Response
<!-- START GET /cloud_files/2.json -->
```json
{
  "id": 1069480357,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-07-21T00:01:30.563Z",
  "updated_at": "2026-07-21T00:01:30.713Z",
  "title": "Brand book draft",
  "inherits_status": true,
  "type": "CloudFile",
  "url": "https://www.dropbox.com/s/abcd1234/brand-draft.pdf",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/cloud_files/1069480357",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDM1Nz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--bae2da8bce151155208b5e345f541375a8e8b9a6.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480357/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480357/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480357/boosts.json",
  "position": 2,
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
  "description": "<div dir=\"auto\">Working draft of the brand guidelines</div>",
  "description_attachments": [],
  "service": {
    "name": "Dropbox",
    "example_url": "https://www.dropbox.com/s/abcd1234/example.pdf",
    "code": "dropbox",
    "valid_patterns": [
      "(.*?\\.)?dropbox\\.com(\\/.*)?"
    ],
    "supporting_text": "a file or folder on Dropbox"
  }
}
```
<!-- END GET /cloud_files/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/cloud_files/2.json
```

Create a cloud file
-------------------

* `POST /buckets/1/vaults/3/cloud_files.json` will create a new cloud file under the
  [vault][vaults] with ID `3` in the [project][projects] with ID `1`.

###### Required parameters

| Param        | Type   | Description |
| ------------ | ------ | ----------- |
| `url`        | String | The URL of the file or document on the external service. |
| `service`    | String | A short identifier for the external service (e.g. `dropbox`, `google_doc`, `figma`, or `other`). The `url` is validated against the selected service's URL patterns, so it must be a valid link for that service. Use `other` for links that don't match a recognized service — it accepts any well-formed web (HTTPS) URL and is stored as a generic cloud file. |

###### Optional parameters

| Param         | Type    | Description |
| ------------- | ------- | ----------- |
| `title`       | String | The cloud file's title. Defaults to `Untitled` when omitted. |
| `description` | HTML    | Rich-text description for the cloud file. |
| `subscriptions` | Array<Integer> | IDs of [people][people] to subscribe to comments and boosts. |
| `visible_to_clients` | Boolean | A **top-level** field — a sibling of the `cloud_file` object, *not* inside it. When the project has clients enabled, whether the cloud file is visible to them. Defaults to `false`; a **client** caller always creates client-visible records. Applies only when creating directly in the tool's vault; items created inside a folder inherit the folder's visibility. See [Client visibility][client_visibility]. |

[projects]: projects.md
[people]: people.md
[client_visibility]: client_visibility.md

###### Example JSON Request
<!-- START POST PAYLOAD /buckets/1/vaults/3/cloud_files.json -->
```json
{
  "cloud_file": {
    "title": "Brand assets",
    "description": "<div>Logos and color tokens</div>",
    "url": "https://www.dropbox.com/s/abcd1234/brand.zip",
    "service": "dropbox"
  },
  "visible_to_clients": true
}
```
<!-- END POST PAYLOAD /buckets/1/vaults/3/cloud_files.json -->

A successful create returns `201 Created` with the new cloud file's JSON shape:

###### Example JSON Response
<!-- START POST /buckets/1/vaults/3/cloud_files.json -->
```json
{
  "id": 1069480436,
  "status": "active",
  "visible_to_clients": true,
  "created_at": "2026-07-21T01:06:09.387Z",
  "updated_at": "2026-07-21T01:06:09.422Z",
  "title": "Brand assets",
  "inherits_status": true,
  "type": "CloudFile",
  "url": "https://www.dropbox.com/s/abcd1234/brand.zip",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/cloud_files/1069480436",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDQzNj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--ca1e22672f2d6e015bdeb03566f87b0b848133fd.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480436/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480436/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480436/boosts.json",
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
  "description": "<div dir=\"auto\">Logos and color tokens</div>",
  "description_attachments": [],
  "service": {
    "name": "Dropbox",
    "example_url": "https://www.dropbox.com/s/abcd1234/example.pdf",
    "code": "dropbox",
    "valid_patterns": [
      "(.*?\\.)?dropbox\\.com(\\/.*)?"
    ],
    "supporting_text": "a file or folder on Dropbox"
  }
}
```
<!-- END POST /buckets/1/vaults/3/cloud_files.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"cloud_file":{"title":"Brand assets","description":"<div>Logos and color tokens</div>","url":"https://www.dropbox.com/s/abcd1234/brand.zip","service":"dropbox"}}' \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/vaults/3/cloud_files.json
```

Update a cloud file
-------------------

* `PUT /cloud_files/2.json` will update the [cloud file][cloud_files] with an ID of `2`.
  The legacy bucket-scoped path `PUT /buckets/1/cloud_files/2.json` is also accepted.

Update accepts `title`, `url`, `service`, and `description`, and all four are sent
on every update — the controller replaces the recordable on each call rather than
patching individual fields. Updating a drafted cloud file also publishes it,
applying any `subscriptions` sent with the request.

###### Example JSON Request
<!-- START PUT PAYLOAD /buckets/1/cloud_files/2.json -->
```json
{
  "cloud_file": {
    "title": "Brand assets v2",
    "description": "<div>Logos, color tokens, and type specimens</div>",
    "url": "https://www.dropbox.com/s/abcd1234/brand-v2.zip",
    "service": "dropbox"
  }
}
```
<!-- END PUT PAYLOAD /buckets/1/cloud_files/2.json -->

Returns `200 OK` with the updated cloud file's JSON shape:

###### Example JSON Response
<!-- START PUT /buckets/1/cloud_files/2.json -->
```json
{
  "id": 1069480436,
  "status": "active",
  "visible_to_clients": true,
  "created_at": "2026-07-21T01:06:09.387Z",
  "updated_at": "2026-07-21T01:06:10.012Z",
  "title": "Brand assets v2",
  "inherits_status": true,
  "type": "CloudFile",
  "url": "https://www.dropbox.com/s/abcd1234/brand-v2.zip",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/cloud_files/1069480436",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDQzNj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--ca1e22672f2d6e015bdeb03566f87b0b848133fd.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480436/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480436/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480436/boosts.json",
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
  "description": "<div dir=\"auto\">Logos, color tokens, and type specimens</div>",
  "description_attachments": [],
  "service": {
    "name": "Dropbox",
    "example_url": "https://www.dropbox.com/s/abcd1234/example.pdf",
    "code": "dropbox",
    "valid_patterns": [
      "(.*?\\.)?dropbox\\.com(\\/.*)?"
    ],
    "supporting_text": "a file or folder on Dropbox"
  }
}
```
<!-- END PUT /buckets/1/cloud_files/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"cloud_file":{"title":"Brand assets v2","description":"<div>Logos, color tokens, and type specimens</div>","url":"https://www.dropbox.com/s/abcd1234/brand-v2.zip","service":"dropbox"}}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/cloud_files/2.json
```
