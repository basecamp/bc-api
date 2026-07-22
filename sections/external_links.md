External links
==============

An external link (historically a **door**) is a [dock tool][tools] that points to an
outside service — a Figma file, a Dropbox folder, a GitHub repository, or any arbitrary
URL. External links show up in a project's "External links" section rather than inside a
[vault][vaults], which makes them the legacy, dock-based sibling of the modern vault-based
[cloud files][cloud_files] and [Google documents][google_documents]. The endpoint URLs
keep the original `doors` resource name.

Because external links are dock tools, they share the generic dock-tool operations
documented in [Tools][tools]: getting, renaming, and trashing a single external link all
go through `/dock/tools/:id.json`. This section covers those cross-links plus the
door-specific parts: the list endpoint and its full shape, the bespoke create path, and
the legacy redirector.

External links are deliberately **omitted from a project's `dock` array**, so the
"discover tools via the dock" advice in [Tools][tools] does not surface them. Use the
list endpoint below to find a project's external links.

Endpoints:

- [List external links](#list-external-links)
- [Get a single external link](#get-a-single-external-link)
- [Create an external link](#create-an-external-link)
- [Rename an external link](#rename-an-external-link)
- [Change a URL, service, or description](#change-a-url-service-or-description)
- [Trash an external link](#trash-an-external-link)

[tools]: tools.md
[cloud_files]: cloud_files.md
[google_documents]: google_documents.md
[recordings]: recordings.md
[vaults]: vaults.md

List external links
-------------------

* `GET /projects/recordings.json?type=Door` will return a [paginated list][pagination] of
  external links across the active [projects][projects] visible to the current user.
  Pass `bucket` to scope to specific projects (which also includes archived ones).

This is the canonical way to enumerate external links and the only endpoint that returns
their **full shape**: the external `url`, the `service` struct, and the `description`. It
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

Get a single external link
--------------------------

Because an external link is a dock tool, fetch one with [Get a tool][get_a_tool]:
`GET /dock/tools/:id.json` returns the recording envelope for the external link.

Note that this envelope's `url` is the external link's Basecamp **redirector** URL — not
the outside address it points to — and it **omits** the `service` and `description`
fields. When you need the external target, the service struct, or the description, use
[List external links](#list-external-links) instead.

The legacy bucket-scoped route is a redirector rather than a JSON resource:

* `GET /buckets/1/dock/doors/2.json` responds with `302 Found` and a `Location` header
  pointing at the external link's outside `url`.

Create an external link
-----------------------

* `POST /buckets/1/dock/doors.json` creates a new external link in the [project][projects]
  with ID `1`.

The create endpoint accepts a JSON body (or `application/x-www-form-urlencoded` form with
bracketed `door[...]` keys) for the ordinary fields, wrapped under a `door` key. Use
`multipart/form-data` when uploading a `door[image]` thumbnail.

###### Required parameters

| Param     | Type   | Description |
| --------- | ------ | ----------- |
| `service` | String | A short identifier for the external service — e.g. `figma`, `dropbox`, `google_drive`, `github`, `notion`, `trello`, `slack`, `zoom` — or `other` for a generic link. |
| `url`     | String | The address the link points to. Supply an HTTP or HTTPS URL; a value without a scheme is prefixed with `https://`. External links do not enforce service-specific URL patterns. |

###### Optional parameters

| Param         | Type   | Description |
| ------------- | ------ | ----------- |
| `title`       | String | The name shown in the External links section. Defaults to `Untitled` when omitted. |
| `description` | HTML   | Rich-text description shown beneath the title. |
| `image`       | Binary | A thumbnail image, uploaded as `multipart/form-data`. |

On success this endpoint returns `302 Found` redirecting to the project with an empty
response body, for every representation. The new external link's ID is **not** returned —
discover it via [List external links](#list-external-links).

###### Example JSON Request

```json
{
  "door": {
    "service": "figma",
    "url": "https://www.figma.com/file/abc123/Design-system",
    "title": "Design system",
    "description": "<div>Shared Figma workspace</div>"
  }
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"door":{"service":"figma","url":"https://www.figma.com/file/abc123/Design-system","title":"Design system","description":"<div>Shared Figma workspace</div>"}}' \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/dock/doors.json
```

Rename an external link
-----------------------

Renaming is a shared dock-tool operation: use [Update a tool][update_a_tool].
`PUT /dock/tools/:id.json` with a `title` renames the external link and returns
`200 OK` with the recording envelope. This changes only the title — see below for the
`url`, `service`, and `description`.

Change a URL, service, or description
-------------------------------------

There is **no reliable JSON endpoint** for changing an external link's `url`, `service`,
or `description`. The door route `PUT /buckets/1/dock/doors/2.json` applies the change but
then returns `406 Not Acceptable` (the record is updated before content negotiation), so
it can't be depended on as a JSON API. Make these edits in the Basecamp web app, or trash
the external link and [create](#create-an-external-link) a new one.

Trash an external link
----------------------

* `DELETE /dock/tools/2.json` (or the legacy `DELETE /buckets/1/dock/doors/2.json`)
  trashes the external link.

This soft-deletes the external link: its `status` becomes `"deleted"` and it no longer
appears in the project's External links section, but the record is not permanently
removed. This differs from [Trash a tool][trash_a_tool], which permanently removes a
regular tool — only the request shape is shared.

This endpoint returns `204 No Content` if successful.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/dock/tools/2.json
```

[projects]: projects.md
[pagination]: ../README.md#pagination
[get_recordings]: recordings.md#get-recordings
[get_a_tool]: tools.md#get-a-tool
[update_a_tool]: tools.md#update-a-tool
[trash_a_tool]: tools.md#trash-a-tool
