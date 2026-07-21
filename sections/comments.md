Comments
========

To determine if a resource can be commented on, check for the presence of `comments_count` and `comments_url` attributes in its JSON response.

Endpoints:

- [Get comments](#get-comments)
- [Get a comment](#get-a-comment)
- [Create a comment](#create-a-comment)
- [Update a comment](#update-a-comment)
- [Trash a comment][trash]

Get comments
------------

* `GET /recordings/3/comments.json` will return a [paginated list][pagination] of active comments for the recording with ID of `3`.

###### Example JSON Response
<!-- START GET /recordings/3/comments.json -->
```json
[
  {
    "id": 1069479843,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-04-14T21:24:00.000Z",
    "updated_at": "2026-04-14T21:24:00.000Z",
    "title": "Re: We won Leto!",
    "inherits_status": true,
    "type": "Comment",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/comments/1069479843.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069479842#__recording_1069479843",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg0Mz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--9f3559acc7461447eef3e63c725cbaf42f909e88.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479843/boosts.json",
    "parent": {
      "id": 1069479842,
      "title": "We won Leto!",
      "type": "Message",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/messages/1069479842.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069479842"
    },
    "bucket": {
      "id": 2085958505,
      "name": "The Leto Laptop",
      "type": "Project"
    },
    "creator": {
      "id": 1049715916,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxNj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--6414c77c0a206bc7d45987b8335318b768e8651f",
      "name": "Andrew Wong",
      "personable_type": "User",
      "title": "Senior Branding Strategist",
      "tagline": null,
      "location": null,
      "created_at": "2026-05-28T17:22:23.572Z",
      "updated_at": "2026-05-28T17:22:23.572Z",
      "email_address": "andrew@honchodesign.com",
      "bio": null,
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMxkkT4=--0ea74d7e5d39ad2d120da79250b179b7e0b00c44/avatar",
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    },
    "content": "Yeah! Great job everyone! Super excited to get going!",
    "content_attachments": []
  }
]
```
<!-- END GET /recordings/3/comments.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/recordings/3/comments.json
```


Get a comment
-------------

* `GET /comments/2.json` will return the comment with an ID of `2`.

###### Example JSON Response
<!-- START GET /comments/2.json -->
```json
{
  "id": 1069479852,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-04-15T01:18:00.000Z",
  "updated_at": "2026-04-15T01:18:00.000Z",
  "title": "Re: We won Leto!",
  "inherits_status": true,
  "type": "Comment",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/comments/1069479852.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069479842#__recording_1069479852",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg1Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--94ecf8956b99a44c68d14588fb31b3b3439d70a4.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479852/boosts.json",
  "parent": {
    "id": 1069479842,
    "title": "We won Leto!",
    "type": "Message",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/messages/1069479842.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069479842"
  },
  "bucket": {
    "id": 2085958505,
    "name": "The Leto Laptop",
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
  "content": "I just want to echo what just about everyone already said. This is a big one for us, and I can't wait to get going. I'll be spinning up the project shortly!",
  "content_attachments": []
}
```
<!-- END GET /comments/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/comments/2.json
```


Create a comment
----------------

* `POST /recordings/3/comments.json` publishes a comment under the recording with an ID of `3`.

**Required parameters**: `content` as the body of the comment. See our [Rich text guide][rich] for what HTML tags are allowed.

Note: All people who are subscribed to the recording will be notified when the comment is posted.

This endpoint will return `201 Created` with the current JSON representation of the comment if the creation was a success. See the [Get a comment](#get-a-comment) endpoint for more info on the payload. The `Location` header will contain a URL to the HTML version of the new comment.

###### Example JSON Request

```json
{
  "content": "<div><em>Wow!</em> That is cool.</div>"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"content":"<div><em>Wow!</em> That is cool.</div>"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/3/comments.json
```


Update a comment
----------------

* `PUT /comments/2.json` allows changing content of the comment with an ID of `2`.

This endpoint will return `200 OK` with the current JSON representation of the comment if the update was a success. See the [Get a comment](#get-a-comment) endpoint for more info on the payload. The `Location` header will contain a URL to the HTML version of the updated comment.

###### Example JSON Request

```json
{
  "content": "<div><em>No way!</em> That isn't cool at all.</div>"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"content":"<div><em>No way!</em> That isn't cool at all.</div>"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/comments/2.json
```


Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/recordings/3/comments.json` → [Get comments](#get-comments)
* `GET /buckets/1/comments/2.json` → [Get a comment](#get-a-comment)
* `POST /buckets/1/recordings/3/comments.json` → [Create a comment](#create-a-comment)
* `PUT /buckets/1/comments/2.json` → [Update a comment](#update-a-comment)

[recordings]: recordings.md#recordings
[messages]:   messages.md#messages
[todolists]:  todolists.md#todolists
[todos]:      todos.md#todos
[trash]:      recordings.md#trash-a-recording
[pagination]: ../README.md#pagination
[rich]:       rich_text.md
