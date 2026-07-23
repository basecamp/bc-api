My folders
==========

Available since Basecamp 5: **folders** group [projects][projects] together on a
person's home screen. Folders are per-user — each person arranges their own home
into folders, and filing a project into a folder for yourself doesn't change how
anyone else sees it. Membership, ordering, and appearance all belong to the
authenticated user.

For historical reasons the path and the wire type say `stack(s)` rather than
`folder(s)`; they are the same thing.

Endpoints:

- [Get my folders](#get-my-folders)
- [Get a folder](#get-a-folder)
- [Create a folder](#create-a-folder)
- [Update a folder](#update-a-folder)
- [Delete a folder](#delete-a-folder)

[projects]: projects.md

Get my folders
--------------

* `GET /my/stacks.json` returns the authenticated user's folders, in the order
  they appear on the home screen.

###### Example JSON Response
<!-- START GET /my/stacks.json -->
```json
[
  {
    "id": 2085958508,
    "name": "Client work",
    "type": "Stack",
    "created_at": "2026-07-22T22:43:02.439Z",
    "updated_at": "2026-07-22T22:43:02.572Z",
    "bucket_ids": [],
    "is_emoji_only_name": false,
    "star_url": "https://3.basecampapi.com/195539477/buckets/2085958508/stars.json",
    "gauges_url": null,
    "color": null,
    "image_url": null,
    "url": "https://3.basecampapi.com/195539477/my/stacks/2085958508.json"
  }
]
```
<!-- END GET /my/stacks.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/stacks.json
```

Get a folder
------------

* `GET /my/stacks/2.json` returns the folder with an ID of `2`, including the
  [projects][projects] grouped inside it under `projects`.

###### Example JSON Response
<!-- START GET /my/stacks/2.json -->
```json
{
  "id": 2085958508,
  "name": "Client work",
  "type": "Stack",
  "created_at": "2026-07-22T22:43:02.439Z",
  "updated_at": "2026-07-22T22:43:02.572Z",
  "bucket_ids": [],
  "is_emoji_only_name": false,
  "star_url": "https://3.basecampapi.com/195539477/buckets/2085958508/stars.json",
  "gauges_url": null,
  "color": null,
  "image_url": null,
  "url": "https://3.basecampapi.com/195539477/my/stacks/2085958508.json",
  "projects": []
}
```
<!-- END GET /my/stacks/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/stacks/2.json
```

Create a folder
---------------

* `POST /my/stacks.json` creates a new folder for the authenticated user and
  files the given [projects][projects] into it. The folder is placed at the top
  of the home screen.

###### Optional parameters

| Param         | Type            | Description |
| ------------- | --------------- | ----------- |
| `name`        | String          | The folder's name. Defaults to `New folder` when blank or omitted. |
| `project_ids` | Array<Integer> | IDs of the projects to file into the folder. Each must be a project the user can access, or an all-access project they're eligible to join — filing an all-access project the user isn't yet a member of also grants them access to it. Archived, trashed, or invitation-only projects the user isn't on are rejected: the whole request returns `404 Not Found` and nothing is created. Omit it, or send `null` or an empty array, for an empty folder. |

###### Example JSON Request
<!-- START POST PAYLOAD /my/stacks.json -->
```json
{
  "name": "Client work",
  "project_ids": []
}
```
<!-- END POST PAYLOAD /my/stacks.json -->

A successful create returns `201 Created` with the new folder's JSON shape,
including its grouped `projects`:

###### Example JSON Response
<!-- START POST /my/stacks.json -->
```json
{
  "id": 2085958508,
  "name": "Client work",
  "type": "Stack",
  "created_at": "2026-07-22T22:43:02.439Z",
  "updated_at": "2026-07-22T22:43:02.572Z",
  "bucket_ids": [],
  "is_emoji_only_name": false,
  "star_url": "https://3.basecampapi.com/195539477/buckets/2085958508/stars.json",
  "gauges_url": null,
  "color": null,
  "image_url": null,
  "url": "https://3.basecampapi.com/195539477/my/stacks/2085958508.json",
  "projects": []
}
```
<!-- END POST /my/stacks.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"name":"Client work","project_ids":[]}' \
  https://3.basecampapi.com/$ACCOUNT_ID/my/stacks.json
```

Update a folder
---------------

* `PUT /my/stacks/2.json` renames the folder with an ID of `2`. Only `name` can
  be changed; a folder's projects, ordering, and image are managed elsewhere.

###### Permitted parameters

| Param  | Type   | Description |
| ------ | ------ | ----------- |
| `name` | String | The folder's new name. |

###### Example JSON Request
<!-- START PUT PAYLOAD /my/stacks/2.json -->
```json
{
  "name": "Active client work"
}
```
<!-- END PUT PAYLOAD /my/stacks/2.json -->

Returns `200 OK` with the updated folder's JSON shape:

###### Example JSON Response
<!-- START PUT /my/stacks/2.json -->
```json
{
  "id": 2085958508,
  "name": "Active client work",
  "type": "Stack",
  "created_at": "2026-07-22T22:43:02.439Z",
  "updated_at": "2026-07-22T22:43:02.572Z",
  "bucket_ids": [],
  "is_emoji_only_name": false,
  "star_url": "https://3.basecampapi.com/195539477/buckets/2085958508/stars.json",
  "gauges_url": null,
  "color": null,
  "image_url": null,
  "url": "https://3.basecampapi.com/195539477/my/stacks/2085958508.json",
  "projects": []
}
```
<!-- END PUT /my/stacks/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"name":"Active client work"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/my/stacks/2.json
```

Delete a folder
---------------

* `DELETE /my/stacks/2.json` deletes the folder with an ID of `2` and returns
  `204 No Content`. Deleting a folder **unpins its projects** from the person's
  home screen — the projects themselves are not deleted, and they are not moved
  back out onto the home screen; they simply stop appearing there until pinned
  again.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/my/stacks/2.json
```
