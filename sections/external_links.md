External links
==============

An external link (historically a **door**) is a [dock tool][tools] that points to an
outside service — a Figma file, a Dropbox folder, a GitHub repository, or any arbitrary
URL. External links show up in a project's "External links" section rather than inside a
[vault][vaults], which makes them the legacy, dock-based sibling of the modern vault-based
[cloud files][cloud_files] and [Google documents][google_documents]. The endpoint URLs
keep the original `doors` resource name.

External links are deliberately **omitted from a project's `dock` array**, so the
"discover tools via the dock" advice in [Tools][tools] does not surface them. Use
[Get external links in a project](#get-external-links-in-a-project) to find them.

Every endpoint below returns an external link's **full shape**: the outside address in
`url`, the `service` struct, and the `description`. Because external links are dock
tools, the generic dock-tool operations in [Tools][tools] also work on them, but those
return the plain recording envelope, whose `url` is the API URL and which omits `service`
and `description`.

Endpoints:

- [Get external links in a project](#get-external-links-in-a-project)
- [List external links across projects](#list-external-links-across-projects)
- [Get an external link](#get-an-external-link)
- [Create an external link](#create-an-external-link)
- [Update an external link](#update-an-external-link)
- [Trash an external link](#trash-an-external-link)

[tools]: tools.md
[cloud_files]: cloud_files.md
[google_documents]: google_documents.md
[recordings]: recordings.md
[vaults]: vaults.md

Get external links in a project
-------------------------------

* `GET /buckets/1/dock/doors.json` will return the active external links in the
  [project][projects] with ID `1`, in the order they appear in its External links
  section.

The list isn't paginated: a project has a handful of external links at most. Clients see
only the external links that are visible to them.

###### Example JSON Response
<!-- START GET /buckets/1/dock/doors.json -->
```json
[
  {
    "id": 1069480290,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-07-22T15:51:54.872Z",
    "updated_at": "2026-07-22T15:51:54.886Z",
    "title": "Design system",
    "inherits_status": true,
    "type": "Door",
    "url": "https://www.figma.com/file/abc123/Design-system",
    "app_url": "https://3.basecampapi.com/195539477/buckets/2085958504/dock/doors/1069480290",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI5MD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--01c7c586d5f3a3e368c70860a5055ff3ca520d55.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480290/subscription.json",
    "position": 8,
    "bucket": {
      "id": 2085958504,
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
      "created_at": "2026-07-22T15:48:06.186Z",
      "updated_at": "2026-07-22T15:48:07.012Z",
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
    "service": {
      "name": "Figma",
      "example_url": "https://www.figma.com/file/aGVsbG8gZmlnbWEgZmlsZQ",
      "code": "figma",
      "valid_patterns": [
        "(.*?\\.)?figma\\.com(\\/.*)?"
      ],
      "supporting_text": "a file or project on Figma"
    },
    "description": "<div>Shared Figma workspace</div>"
  }
]
```

<!-- END GET /buckets/1/dock/doors.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/dock/doors.json
```

List external links across projects
-----------------------------------

* `GET /projects/recordings.json?type=Door` will return a [paginated list][pagination] of
  external links across the active [projects][projects] visible to the current user.
  Pass `bucket` to scope to specific projects (which also includes archived ones).

Use this to find external links in more than one project at once. It
extends the generic [Get recordings][get_recordings] endpoint, so it accepts the same
`bucket`, `status`, `sort`, and `direction` query parameters.

###### Example JSON Response
<!-- START GET /projects/recordings.json?type=Door (external link) -->
```json
[
  {
    "id": 1069480290,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-07-22T15:51:54.872Z",
    "updated_at": "2026-07-22T15:51:54.886Z",
    "title": "Design system",
    "inherits_status": true,
    "type": "Door",
    "url": "https://www.figma.com/file/abc123/Design-system",
    "app_url": "https://3.basecampapi.com/195539477/buckets/2085958504/dock/doors/1069480290",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI5MD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--01c7c586d5f3a3e368c70860a5055ff3ca520d55.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480290/subscription.json",
    "position": 8,
    "bucket": {
      "id": 2085958504,
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
      "created_at": "2026-07-22T15:48:06.186Z",
      "updated_at": "2026-07-22T15:48:07.012Z",
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
    "service": {
      "name": "Figma",
      "example_url": "https://www.figma.com/file/aGVsbG8gZmlnbWEgZmlsZQ",
      "code": "figma",
      "valid_patterns": [
        "(.*?\\.)?figma\\.com(\\/.*)?"
      ],
      "supporting_text": "a file or project on Figma"
    },
    "description": "<div>Shared Figma workspace</div>"
  }
]
```
<!-- END GET /projects/recordings.json?type=Door (external link) -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  "https://3.basecampapi.com/$ACCOUNT_ID/projects/recordings.json?type=Door"
```

Get an external link
--------------------

* `GET /dock/doors/2.json` will return the external link with an ID of `2`.

###### Example JSON Response
<!-- START GET /dock/doors/2.json -->
```json
{
  "id": 1069480290,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-07-22T15:51:54.872Z",
  "updated_at": "2026-07-22T15:51:54.886Z",
  "title": "Design system",
  "inherits_status": true,
  "type": "Door",
  "url": "https://www.figma.com/file/abc123/Design-system",
  "app_url": "https://3.basecampapi.com/195539477/buckets/2085958504/dock/doors/1069480290",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI5MD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--01c7c586d5f3a3e368c70860a5055ff3ca520d55.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480290/subscription.json",
  "position": 8,
  "bucket": {
    "id": 2085958504,
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
    "created_at": "2026-07-22T15:48:06.186Z",
    "updated_at": "2026-07-22T15:48:07.012Z",
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
  "service": {
    "name": "Figma",
    "example_url": "https://www.figma.com/file/aGVsbG8gZmlnbWEgZmlsZQ",
    "code": "figma",
    "valid_patterns": [
      "(.*?\\.)?figma\\.com(\\/.*)?"
    ],
    "supporting_text": "a file or project on Figma"
  },
  "description": "<div>Shared Figma workspace</div>"
}
```
<!-- END GET /dock/doors/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  https://3.basecampapi.com/$ACCOUNT_ID/dock/doors/2.json
```

The bucket-scoped `GET /buckets/1/dock/doors/2.json` is a different thing: a redirector
for people, not a JSON resource. It responds with `302 Found` and a `Location` header
pointing at the external link's outside `url`, which is where an external link's
`app_url` leads.

Create an external link
-----------------------

* `POST /buckets/1/dock/doors.json` creates a new external link at the end of the
  External links section of the [project][projects] with ID `1`.

Send the external link's fields wrapped under a `door` key, and `visible_to_clients`
beside it. Use `multipart/form-data` with bracketed `door[...]` keys when uploading a
`door[image]` thumbnail.

###### Required parameters

| Param          | Type   | Description |
| -------------- | ------ | ----------- |
| `door.service` | String | A short identifier for the external service — e.g. `figma`, `dropbox`, `google_drive`, `github`, `notion`, `trello`, `slack`, `zoom` — or `other` for a generic link. |
| `door.url`     | String | The address the link points to. Supply an HTTP or HTTPS URL; a value without a scheme is prefixed with `https://`. External links do not enforce service-specific URL patterns. |

###### Optional parameters

| Param                | Type    | Description |
| -------------------- | ------- | ----------- |
| `door.title`         | String  | The name shown in the External links section. Defaults to `Untitled` when omitted. |
| `door.description`   | HTML    | Rich-text description shown beneath the title. |
| `door.image`         | Binary  | A thumbnail image, uploaded as `multipart/form-data`. |
| `visible_to_clients` | Boolean | Whether the project's clients can see the external link. Defaults to `false`, keeping it private to the team, whatever the visibility of the project's other tools. An external link a client creates is always visible to clients. |

This endpoint will return `201 Created` with the current JSON representation of the
external link if the creation was a success. See the
[Get an external link](#get-an-external-link) endpoint for more info on the payload.
An unusable `url` returns `422 Unprocessable Entity`.

###### Example JSON Request
<!-- START POST PAYLOAD /buckets/1/dock/doors.json -->
```json
{
  "door": {
    "service": "github",
    "title": "Source code",
    "url": "https://github.com/honcho/leto-laptop",
    "description": "<div>Firmware and tooling</div>"
  },
  "visible_to_clients": false
}
```
<!-- END POST PAYLOAD /buckets/1/dock/doors.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"door":{"service":"github","title":"Source code","url":"https://github.com/honcho/leto-laptop","description":"<div>Firmware and tooling</div>"},"visible_to_clients":false}' \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/dock/doors.json
```

Update an external link
-----------------------

* `PUT /dock/doors/2.json` allows changing the external link with an ID of `2`.

Send only what changes: every parameter is optional, and those left out keep their
values. Leave out `door` entirely to change only `visible_to_clients`.

###### Optional parameters

| Param                | Type    | Description |
| -------------------- | ------- | ----------- |
| `door.service`       | String  | The external service, as for [create](#create-an-external-link). |
| `door.url`           | String  | The address the link points to. |
| `door.title`         | String  | The name shown in the External links section. |
| `door.description`   | HTML    | Rich-text description shown beneath the title. |
| `door.image`         | Binary  | A new thumbnail image, uploaded as `multipart/form-data`. |
| `visible_to_clients` | Boolean | Whether the project's clients can see the external link. |

This endpoint will return `200 OK` with the current JSON representation of the external
link if the update was a success. See the [Get an external link](#get-an-external-link)
endpoint for more info on the payload. An unusable `url` returns
`422 Unprocessable Entity`.

###### Example JSON Request
<!-- START PUT PAYLOAD /dock/doors/2.json -->
```json
{
  "door": {
    "title": "Firmware",
    "url": "https://github.com/honcho/leto-laptop-firmware"
  },
  "visible_to_clients": true
}
```
<!-- END PUT PAYLOAD /dock/doors/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -X PUT -d '{"door":{"title":"Firmware","url":"https://github.com/honcho/leto-laptop-firmware"},"visible_to_clients":true}' \
  https://3.basecampapi.com/$ACCOUNT_ID/dock/doors/2.json
```

Renaming also works through the generic [Update a tool][update_a_tool], which changes
only the title.

Trash an external link
----------------------

* `DELETE /dock/doors/2.json` trashes the external link with an ID of `2`. The
  bucket-scoped `DELETE /buckets/1/dock/doors/2.json` and the generic
  `DELETE /dock/tools/2.json` do the same.

This deletes the external link: its `status` becomes `"deleted"` and it no longer
appears in the project's External links section. It doesn't go to the trash, and Basecamp
permanently destroys it about five days later. Deleting a regular tool through
[Trash a tool][trash_a_tool] doesn't always delete it.

This endpoint returns `204 No Content` if successful.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/dock/doors/2.json
```

[projects]: projects.md
[pagination]: ../README.md#pagination
[get_recordings]: recordings.md#get-recordings
[update_a_tool]: tools.md#update-a-tool
[trash_a_tool]: tools.md#trash-a-tool
