My bookmarks
============

Endpoints for listing the current user's bookmarked recordings and for
bookmarking or unbookmarking an individual recording.

A bookmark links the current user to a single recording (such as a message,
to-do, document, or card). Bookmarks are personal: they are visible only to the
user who created them.

Endpoints:

- [Get bookmarks](#get-bookmarks)
- [Get a bookmark](#get-a-bookmark)
- [Create a bookmark](#create-a-bookmark)
- [Delete a bookmark](#delete-a-bookmark)


Get bookmarks
-------------

* `GET /my/bookmarks.json` will return a paginated list of the current user's
  bookmarked recordings, most recently bookmarked first.

Each entry wraps the [recording](recordings.md) that was bookmarked along with
the bookmark's own `id`, `created_at`, and `updated_at`. See [pagination](../README.md#pagination)
for how the `X-Total-Count` and `Link` response headers work.

###### Example JSON Response
<!-- START GET /my/bookmarks.json -->
```json
[
  {
    "id": 430859449,
    "created_at": "2026-07-22T22:14:19.716Z",
    "updated_at": "2026-07-22T22:14:19.716Z",
    "recording": {
      "id": 1069479842,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-06-08T21:14:00.000Z",
      "updated_at": "2026-07-22T21:57:48.150Z",
      "title": "We won Leto!",
      "inherits_status": true,
      "type": "Message",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/messages/1069479842.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/messages/1069479842",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1708f8c9adb5dd70ebcc6837a0c054bacaf792fe.json",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479842/subscription.json",
      "parent": {
        "id": 1069479828,
        "title": "Message Board",
        "type": "Message::Board",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/message_boards/1069479828.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/message_boards/1069479828"
      },
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
        "created_at": "2026-07-22T21:49:53.455Z",
        "updated_at": "2026-07-22T21:49:55.003Z",
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
      }
    }
  }
]
```
<!-- END GET /my/bookmarks.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/bookmarks.json
```


Get a bookmark
--------------

* `GET /recordings/2/bookmark.json` will report whether the recording with the
  given ID is bookmarked by the current user.

The response is `{ "bookmarked": true }` when the recording is bookmarked and
`{ "bookmarked": false }` otherwise.

###### Example JSON Response
<!-- START GET /recordings/2/bookmark.json -->
```json
{
  "bookmarked": true
}
```
<!-- END GET /recordings/2/bookmark.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/bookmark.json
```


Create a bookmark
-----------------

* `POST /recordings/2/bookmark.json` will bookmark the recording with the given
  ID for the current user.

No parameters are required. This endpoint returns `201 Created` with the
bookmark. Bookmarking is idempotent — re-bookmarking a recording you've already
bookmarked returns the existing bookmark and does not create a duplicate.

###### Example JSON Response
<!-- START POST /recordings/2/bookmark.json -->
```json
{
  "id": 430859450,
  "created_at": "2026-07-22T22:14:20.315Z",
  "updated_at": "2026-07-22T22:14:20.315Z",
  "recording": {
    "id": 1069479859,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-06-09T05:40:00.000Z",
    "updated_at": "2026-06-09T05:40:00.000Z",
    "title": "Win pitch",
    "inherits_status": true,
    "type": "Todo",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todos/1069479859.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todos/1069479859",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg1OT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--078daba619bc94cd015e87263bee35332b52c51f.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479859/subscription.json",
    "parent": {
      "id": 1069479829,
      "title": "To-dos",
      "type": "Todoset",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958504/todosets/1069479829.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/todosets/1069479829"
    },
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
      "created_at": "2026-07-22T21:49:53.455Z",
      "updated_at": "2026-07-22T21:49:55.003Z",
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
    }
  }
}
```
<!-- END POST /recordings/2/bookmark.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/bookmark.json
```


Delete a bookmark
-----------------

* `DELETE /recordings/2/bookmark.json` will remove the current user's bookmark
  for the recording with the given ID.

This endpoint returns `204 No Content` if the removal was a success. Deleting a
bookmark that doesn't exist will also return `204 No Content`.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/bookmark.json
```
