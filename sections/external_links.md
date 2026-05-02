External links
==============

External links (previously known as **doors**) are quick links to outside services like Dropbox, Google Drive, Trello, or any arbitrary URL that appear in a project's "External links" section. Each external link has a service type, URL, title, and optional description.

External links are a separate collection from tools and do not appear in the project's `dock` array. The endpoint URLs continue to use the original `doors` resource name.

Endpoints:

- [Get an external link](#get-an-external-link)
- [Create an external link](#create-an-external-link)
- [Update an external link](#update-an-external-link)
- [Trash an external link](#trash-an-external-link)


Get an external link
--------------------

* `GET /buckets/1/dock/doors/2.json` for the external link with ID `2` in the project with ID `1`.

This endpoint behaves as a redirector rather than returning a JSON resource: it responds with `302 Found` and a `Location` header pointing to the external link's `url`. There is currently no public endpoint that returns the JSON representation of a single external link.

To retrieve external link metadata (id, title, url, service, status), use [Search](search.md#search) and filter results by `type: "Door"`. The shape returned in search results is shown below.

###### Example JSON Response
<!-- START GET /search.json (Door result) -->
```json
{
  "id": 1069479500,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-02-12T06:09:34.667Z",
  "updated_at": "2026-02-12T06:13:57.731Z",
  "title": "Design system",
  "inherits_status": true,
  "type": "Door",
  "url": "https://www.figma.com/file/abc",
  "app_url": "https://3.basecampapi.com/195539477/buckets/2085958504/dock/doors/1069479500",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTUwMD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--placeholder.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479500/subscription.json",
  "position": 1,
  "bucket": {
    "id": 2085958504,
    "name": "The Leto Laptop",
    "type": "Project"
  },
  "creator": {
    "id": 1049715913,
    "name": "Victor Cooper",
    "email_address": "victor@honchodesign.com"
  },
  "service": {
    "name": "Figma",
    "example_url": "https://www.figma.com/file/...",
    "code": "figma",
    "valid_patterns": ["www\\.figma\\.com\\/file\\/.+"],
    "supporting_text": null
  },
  "description": null,
  "content": null
}
```
<!-- END GET /search.json (Door result) -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -A "MyApp (yourname@example.com)" \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/dock/doors/2.json
```


Create an external link
-----------------------

* `POST /buckets/1/dock/doors.json` creates a new external link in the project with ID `1`.

**Required parameters**:
* `door[service]` - the service type. Use `other` for a generic external link, or one of `dropbox`, `google_drive`, `trello`, `github`, `figma`, `airtable`, `notion`, `slack`, `zoom`. Unrecognized values return `422 Unprocessable Entity`.
* `door[url]` - the URL the link points to.
* `door[title]` - the title shown in the External links section.

_Optional parameters_:
* `door[description]` - a short description shown beneath the title.
* `door[image]` - a thumbnail image (binary, multipart upload).

Unlike most BC3 endpoints, this endpoint expects parameters in `application/x-www-form-urlencoded` form (with bracketed keys), not JSON. It returns `302 Found` redirecting to the project's dock edit page on success with an empty response body. The new external link's ID is not returned — discover it via [Search](search.md#search).

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -A "MyApp (yourname@example.com)" \
  --data-urlencode "door[service]=other" \
  --data-urlencode "door[url]=https://example.com" \
  --data-urlencode "door[title]=External link" \
  --data-urlencode "door[description]=Optional description" \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/dock/doors.json
```


Update an external link
-----------------------

* `PUT /buckets/1/dock/doors/2.json` updates the external link with ID `2` in the project with ID `1`.

Any of the [Create an external link](#create-an-external-link) parameters may be supplied. Like create, this endpoint expects `application/x-www-form-urlencoded` parameters with bracketed keys and returns `302 Found` redirecting to the project's dock edit page on success with an empty response body.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -A "MyApp (yourname@example.com)" \
  -X PUT \
  --data-urlencode "door[title]=Updated title" \
  --data-urlencode "door[url]=https://example.com/new-path" \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/dock/doors/2.json
```


Trash an external link
----------------------

* `DELETE /buckets/1/dock/doors/2.json` trashes the external link with ID `2` in the project with ID `1`.

This endpoint will return `204 No Content` if successful. Trashed external links are soft-deleted: their `status` becomes `"deleted"` (visible in [Search](search.md#search) results) and they no longer appear in the project's External links section.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -A "MyApp (yourname@example.com)" \
  -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/dock/doors/2.json
```
