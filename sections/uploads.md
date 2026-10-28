Uploads
=======

Endpoints:

- [Get uploads](#get-uploads)
- [Get an upload](#get-an-upload)
- [Get upload versions](#get-upload-versions)
- [Create an upload version](#create-an-upload-version)
- [Create an upload](#create-an-upload)
- [Update an upload](#update-an-upload)
- [Move an upload][move]
- [Trash an upload][trash]

Get uploads
-----------

* `GET /vaults/2/uploads.json` will return a [paginated list][pagination] of active uploads in the [vault][vaults] with ID of `2`.

###### Example JSON Response
<!-- START GET /vaults/2/uploads.json -->
```json
[
  {
    "id": 1069480281,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-05-28T17:29:05.129Z",
    "updated_at": "2026-05-28T17:29:05.144Z",
    "title": "company-logo.png",
    "inherits_status": true,
    "type": "Upload",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/uploads/1069480281.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/uploads/1069480281",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI4MT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--424f03d79a7bf89ae7d9c7dcf5637a805a91a198.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480281/subscription.json",
    "comments_count": 0,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480281/comments.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480281/boosts.json",
    "position": 3,
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
    "description": "<div dir=\"auto\">Check out the new logo</div>",
    "description_attachments": [],
    "content_type": "image/png",
    "byte_size": 1281,
    "filename": "company-logo.png",
    "download_url": "https://3.basecampapi.com/195539477/buckets/2085958505/uploads/1069480281/download/company-logo.png",
    "app_download_url": "https://storage.3.basecamp.com/195539477/buckets/2085958505/uploads/1069480281/download/company-logo.png",
    "width": 164,
    "height": 39
  }
]
```
<!-- END GET /vaults/2/uploads.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/vaults/2/uploads.json
```

Get an upload
-------------

* `GET /uploads/2.json` will return the upload with an ID of `2`.

###### Example JSON Response
<!-- START GET /uploads/2.json -->
```json
{
  "id": 1069480281,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-28T17:29:05.129Z",
  "updated_at": "2026-05-28T17:29:05.144Z",
  "title": "company-logo.png",
  "inherits_status": true,
  "type": "Upload",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/uploads/1069480281.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/uploads/1069480281",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI4MT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--424f03d79a7bf89ae7d9c7dcf5637a805a91a198.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480281/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480281/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480281/boosts.json",
  "position": 3,
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
  "description": "<div dir=\"auto\">Check out the new logo</div>",
  "description_attachments": [],
  "content_type": "image/png",
  "byte_size": 1281,
  "filename": "company-logo.png",
  "download_url": "https://3.basecampapi.com/195539477/buckets/2085958505/uploads/1069480281/download/company-logo.png",
  "app_download_url": "https://storage.3.basecamp.com/195539477/buckets/2085958505/uploads/1069480281/download/company-logo.png",
  "width": 164,
  "height": 39
}
```
<!-- END GET /uploads/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/uploads/2.json
```

Get upload versions
-------------------

* `GET /uploads/2/versions.json` will return a list of version events for the upload with an ID of `2`, in reverse chronological order.

Three `action`s appear here: `created` and `active` mark the upload's publication, and `blob_changed` marks a file replacement. Filter on `action == "blob_changed"` to list only the replacements.

Each version event carries an `upload` object describing the file that version recorded:

* `filename`, `content_type` and `byte_size` — the file as it was at that version.
* `download_url` — downloads that specific version's file, unlike the upload's own `download_url`, which always serves the latest one.
* `app_download_url` — the equivalent link for the Basecamp web app.
* `current` — `true` for the most recent version, `false` for the rest. Exactly one version is current. Note that this is the newest *version*, which isn't necessarily the file you get from the upload's own `download_url`: [updating an upload](#update-an-upload) changes its metadata without recording a new version.

The whole `upload` object is omitted — not `null` — on the rare version whose file has since been removed from the account. The version event itself is still listed, so treat `upload` as optional when decoding.

###### Example JSON Response
<!-- START GET /uploads/2/versions.json -->
```json
[
  {
    "id": 1052473756,
    "recording_id": 1069480281,
    "action": "created",
    "details": {},
    "created_at": "2026-05-28T17:29:05.149Z",
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
    "upload": {
      "content_type": "image/png",
      "byte_size": 1281,
      "filename": "company-logo.png",
      "download_url": "https://3.basecampapi.com/195539477/buckets/2085958505/uploads/1069480281/versions/1052473756/download/company-logo.png",
      "app_download_url": "https://storage.3.basecamp.com/195539477/buckets/2085958505/uploads/1069480281/versions/1052473756/download/company-logo.png",
      "current": true
    }
  }
]
```
<!-- END GET /uploads/2/versions.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/uploads/2/versions.json
```

Create an upload version
------------------------

* `POST /uploads/2/versions.json` replaces the file of the upload with an ID of `2`.

The upload keeps its ID, its URL and its comments, and the previous file stays available as a past version. Use this instead of [creating a new upload](#create-an-upload) when you're publishing a new release of the same file and want its link to keep working.

**Required parameters**: `attachable_sgid` for an uploaded attachment. See the [Create an attachment][attachments] endpoint for more info on uploading attachments.

_Optional parameters_:
* `base_name` - a new file name for the upload. `base_name` should be a file name *without* an extension (e.g. `"pizza"` for `"pizza.png"`). Omit it to keep the name of the file you uploaded.
* `description` - containing information about the upload. See our [Rich text guide][rich] for what HTML tags are allowed. Omit it to carry the previous version's description forward, or send `""` or `null` to clear it.
* `notify` - who to notify about the replacement: `default` (people subscribed to project notifications), `everyone`, or `custom` (specific people via `subscriptions`). Omit both `notify` and `subscriptions` to notify nobody.
* `subscriptions` - an array of people IDs to notify about the replacement and subscribe to the upload. Used when `notify` is `custom`, which is also how a `subscriptions` array sent without `notify` is read.

Notified people are subscribed to the upload. Client visibility isn't a parameter here: a replacement never changes who can see the upload, so clients are in the audience only when the upload is already visible to them.

This endpoint will return `201 Created` with the current JSON representation of the upload if the replacement was a success. See the [Get an upload](#get-an-upload) endpoint for more info on the payload.

A replacement stores the new file alongside every past version, so it counts against the account's storage. If the account has reached its storage limit you'll see a `507 Insufficient Storage` and a response of:

```json
{
  "error": "The storage limit for this account has been reached."
}
```

###### Example JSON Request

```json
{
  "attachable_sgid": "BAh2CEkiCGdpZAY6BkVUSSIsZ2lkOi7vYmMzL0F0dGFjaG1lbnQvNzM4NDcyNj9leHBpcmVzX2luBjsAVEkiDHB1cnBvc2UGOwBUSSIPYXR0YWNoYWJsZQY7AFRJIg9leHBpcmVzX2F0BjsAVDA=--13982201abe18044c897e32979c7dccfe8add9c1",
  "description": "<div><strong>Yum</strong></div>",
  "base_name": "yummy_pizza"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"attachable_sgid":"BAh…9c1","description":"<div><strong>Yum</strong></div>","base_name":"yummy_pizza"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/uploads/2/versions.json
```

Create an upload
----------------

* `POST /vaults/2/uploads.json` creates an upload under the vault with an ID of `2`.

**Required parameters**: `attachable_sgid` for an uploaded attachment. See the [Create an attachment][attachments] endpoint for more info on uploading attachments.

_Optional parameters_:
* `description` - containing information about the upload. See our [Rich text guide][rich] for what HTML tags are allowed.
* `base_name` - a new file name for the upload. `base_name` should be a file name *without* an extension (e.g. `"pizza"` for `"pizza.png"`).
* `visible_to_clients` - top-level boolean. When the project has clients enabled, whether the upload is visible to them. Defaults to `false` (team callers creating directly under the docked tool); a **client** caller always creates client-visible records. Applies only when creating directly in the tool's vault; items created inside a folder inherit the folder's visibility. See [Client visibility][client_visibility] to change it after creation.

This endpoint will return `201 Created` with the current JSON representation of the upload if the creation was a success. See the [Get an upload](#get-an-upload) endpoint for more info on the payload. If the account has reached its storage limit you'll see a `507 Insufficient Storage` and a response of:

```json
{
  "error": "The storage limit for this account has been reached."
}
```

###### Example JSON Request

```json
{
  "attachable_sgid": "BAh2CEkiCGdpZAY6BkVUSSIsZ2lkOi7vYmMzL0F0dGFjaG1lbnQvNzM4NDcyNj9leHBpcmVzX2luBjsAVEkiDHB1cnBvc2UGOwBUSSIPYXR0YWNoYWJsZQY7AFRJIg9leHBpcmVzX2F0BjsAVDA=--13982201abe18044c897e32979c7dccfe8add9c1",
  "description": "<div><strong>Yum</strong></div>",
  "base_name": "yummy_pizza"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"attachable_sgid":"BAh…9c1","description":"<div><strong>Yum</strong></div>","base_name":"yummy_pizza"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/vaults/2/uploads.json
```

Update an upload
----------------

* `PUT /uploads/2.json` allows changing the `description` and `base_name` of the upload with an ID of `2`.

This changes the upload's metadata only. To replace the file itself, see [Create an upload version](#create-an-upload-version).

_Optional parameters_:
* `base_name` - a new file name for the upload. `base_name` should be a file name *without* an extension (e.g. `"pizza"` for `"pizza.png"`). Omitting it — or sending `""` — keeps the current name.
* `description` - containing information about the upload. See our [Rich text guide][rich] for what HTML tags are allowed. Omit it to leave the description alone, or send `""` or `null` to clear it.

This endpoint will return `200 OK` with the current JSON representation of the upload if the update was a success. See the [Get an upload](#get-an-upload) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "description": "<div>Meh</div>",
  "base_name": "old_pizza"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"description":"<div>Meh</div>","base_name":"old_pizza"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/uploads/2.json
```

Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/vaults/2/uploads.json` → [Get uploads](#get-uploads)
* `GET /buckets/1/uploads/2.json` → [Get an upload](#get-an-upload)
* `GET /buckets/1/uploads/2/versions.json` → [Get upload versions](#get-upload-versions)
* `POST /buckets/1/uploads/2/versions.json` → [Create an upload version](#create-an-upload-version)
* `POST /buckets/1/vaults/2/uploads.json` → [Create an upload](#create-an-upload)
* `PUT /buckets/1/uploads/2.json` → [Update an upload](#update-an-upload)

[pagination]: ../README.md#pagination
[attachments]: attachments.md#create-an-attachment
[trash]: recordings.md#trash-a-recording
[move]: vaults.md#move-a-document-upload-or-vault
[vaults]: vaults.md#vaults
[rich]: rich_text.md
[client_visibility]: client_visibility.md
