My notifications
=================

The notifications endpoint returns the current user's notification inbox — the same data that powers the sidebar notifications in Basecamp. Notifications are grouped into three categories: unread items, recently read items, and memorized items.

Each notification represents activity on a recording (message, to-do, comment, etc.) that the current user has been notified about. Notifications track unread state, unread counts, and timestamps for when items were read or received.

Endpoints:

- [Get notifications](#get-notifications)
- [Get bubble-ups](#get-bubble-ups)
- [Mark as read](#mark-as-read)


Get notifications
-----------------

* `GET /my/readings.json` will return the current user's notifications grouped into `unreads`, `reads`, `memories`, `bubble_ups`, and `scheduled_bubble_ups`.

Reads are a [paginated list][pagination] with 50 items per page. Unreads are not paginated but are capped at 100 items. Bubble-ups are not paginated here but are capped according to `limit_bubble_ups`. The response includes `bubble_ups_count` and `scheduled_bubble_ups_count` for notification UI counts. Use the [bubble-ups endpoint](#get-bubble-ups) to paginate through all current and scheduled bubble-ups.

_Optional parameters_:

* `page` - page number for paginating through read items. Defaults to `1`.
* `limit_bubble_ups` - set to `true` to cap `bubble_ups` at 2 current bubble-ups and omit the `scheduled_bubble_ups` key. Defaults to `false`.

Each notification in the response includes:

* `id` - the notification ID.
* `created_at` - when the notification was first created.
* `updated_at` - when the notification was last updated.
* `section` - the category: `inbox`, `chats`, `pings`, `remembered`, `mentions`, or `bubbles`.
* `unread_count` - the number of unread updates on this item.
* `unread_at` - timestamp when the item was last marked unread, or `null` if read.
* `read_at` - timestamp when the item was last read, or `null` if unread.
* `readable_sgid` - signed global ID for the readable, used when marking items as read.
* `readable_identifier` - a human-readable identifier for the readable.
* `title` - the title of the readable item.
* `type` - the type of readable (e.g. `Recording`, `Event`).
* `bucket_name` - the name of the project this notification belongs to.
* `creator` - the person who created or last updated the readable (see [People][1] for the full person object).
* `content_excerpt` - a text excerpt of the content, when available.
* `app_url` - the URL to view this item in Basecamp.
* `unread_url` - a URL related to this item's unread state (mark items as read using the "Mark as read" endpoint described below).
* `bookmark_url` - the URL to bookmark this item.
* `memory_url` - the URL to memorize or forget this item (present together with `bubble_up_url` when the item can be bubbled up).
* `bubble_up_url` - the URL to bubble up or pop this item (present together with `memory_url` when the item can be bubbled up).
* `bubble_up_at` - when the item is scheduled to bubble up (only present for scheduled bubble-ups).
* `subscribed` - `true` if the current user is subscribed to the item's container.
* `subscription_url` - the URL to manage the subscription for this item's container.
* `previewable_attachments` - an array of previewable attachments, up to 10.

Pings additionally include:

* `participants` - an array of other people in the ping.
* `named` - whether the ping has a custom name.
* `image_url` - the ping's custom image, if one is set.

###### Example JSON Response
<!-- START GET /my/readings.json -->
```json
{
  "unreads": [],
  "reads": [],
  "memories": [],
  "bubble_ups_count": 1,
  "scheduled_bubble_ups_count": 1,
  "bubble_ups": [
    {
      "id": 20,
      "created_at": "2026-06-10T13:04:06.779Z",
      "updated_at": "2026-06-10T13:04:06.785Z",
      "section": "bubbles",
      "unread_count": 0,
      "unread_at": null,
      "read_at": "2026-06-10T13:04:06.785Z",
      "readable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1708f8c9adb5dd70ebcc6837a0c054bacaf792fe",
      "readable_identifier": "Z2lkOi8vYmMzL1JlY29yZGluZy8xMDY5NDc5ODQy",
      "title": "We won Leto!",
      "type": "Message",
      "icon_type": "message",
      "bucket_name": "The Leto Laptop",
      "creator": {
        "id": 1049715913,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
        "name": "Victor Cooper",
        "email_address": "victor@honchodesign.com",
        "personable_type": "User",
        "title": "Chief Strategist",
        "tagline": "Don't let your dreams be dreams",
        "location": "Chicago, IL",
        "created_at": "2026-06-05T13:28:13.806Z",
        "updated_at": "2026-06-10T13:03:50.424Z",
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
      "content_excerpt": "Hey guys,\n\nWe won the Leto account! This is huge for us, it really marks a turning point for the company.\n\nAs you know we've been pursuing bigger clients in the consumer space, but we've done so carefully. We've never been about getting the biggest clients - those are easy to get. We've been tryi...",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479842/subscription.json",
      "attachments_sample": [],
      "previewable_attachments": [],
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/messages/1069479842",
      "unread_url": "https://3.basecampapi.com/195539477/my/unreads/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1708f8c9adb5dd70ebcc6837a0c054bacaf792fe.json",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1708f8c9adb5dd70ebcc6837a0c054bacaf792fe.json",
      "memory_url": "https://3.basecampapi.com/195539477/my/readings/20/memory.json",
      "bubble_up_url": "https://3.basecampapi.com/195539477/my/readings/20/bubble_up.json",
      "subscribed": true
    }
  ],
  "scheduled_bubble_ups": [
    {
      "id": 23,
      "created_at": "2026-06-10T13:07:28.573Z",
      "updated_at": "2026-06-10T13:07:28.580Z",
      "section": "bubbles",
      "unread_count": 0,
      "unread_at": null,
      "read_at": "2026-06-10T13:07:28.580Z",
      "readable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg2Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--929b3637d6257a5132a133447583416ac5fa7db4",
      "readable_identifier": "Z2lkOi8vYmMzL1JlY29yZGluZy8xMDY5NDc5ODYy",
      "title": "Kickoff: The Leto Microsite!",
      "type": "Message",
      "icon_type": "message",
      "bucket_name": "The Leto Laptop",
      "creator": {
        "id": 1049715938,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--4ccc567a0a3b10e354bca909b704637b601f0b16",
        "name": "Annie Bryan",
        "email_address": "annie@honchodesign.com",
        "personable_type": "User",
        "title": "Central Markets Manager",
        "tagline": "To open a store is easy, to keep it open is an art",
        "location": null,
        "created_at": "2026-06-05T13:28:17.050Z",
        "updated_at": "2026-06-05T13:28:17.050Z",
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
      "content_excerpt": "Hey guys,\n\nWelcome to the project, excited to get going! I'll be managing this, the first project, with Jay as the lead on the account overall.\n\nThere are a lot of components to the account overall, and this is just the first of many. This microsite will serve as a teaser to Leto's newest product...",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479862/subscription.json",
      "attachments_sample": [],
      "previewable_attachments": [],
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/messages/1069479862",
      "unread_url": "https://3.basecampapi.com/195539477/my/unreads/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg2Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--929b3637d6257a5132a133447583416ac5fa7db4.json",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg2Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--929b3637d6257a5132a133447583416ac5fa7db4.json",
      "memory_url": "https://3.basecampapi.com/195539477/my/readings/23/memory.json",
      "bubble_up_url": "https://3.basecampapi.com/195539477/my/readings/23/bubble_up.json",
      "bubble_up_at": "2026-06-15T13:00:00.000Z",
      "subscribed": false
    }
  ]
}
```
<!-- END GET /my/readings.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/readings.json
```

To paginate through read items:

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/readings.json?page=2
```


Get bubble-ups
---------------

* `GET /my/readings/bubble_ups.json` will return the current user's current and scheduled bubble-ups as a [paginated list][pagination] with 50 items per page.

Current bubble-ups are returned first, ordered by most recently bubbled up. Scheduled bubble-ups follow, ordered by scheduled bubble-up time.

Each item uses the same notification object shape as `GET /my/readings.json`.

###### Example JSON Response
<!-- START GET /my/readings/bubble_ups.json -->
```json
[
  {
    "id": 20,
    "created_at": "2026-06-10T13:04:06.779Z",
    "updated_at": "2026-06-10T13:04:06.785Z",
    "section": "bubbles",
    "unread_count": 0,
    "unread_at": null,
    "read_at": "2026-06-10T13:04:06.785Z",
    "readable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1708f8c9adb5dd70ebcc6837a0c054bacaf792fe",
    "readable_identifier": "Z2lkOi8vYmMzL1JlY29yZGluZy8xMDY5NDc5ODQy",
    "title": "We won Leto!",
    "type": "Message",
    "icon_type": "message",
    "bucket_name": "The Leto Laptop",
    "creator": {
      "id": 1049715913,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
      "name": "Victor Cooper",
      "email_address": "victor@honchodesign.com",
      "personable_type": "User",
      "title": "Chief Strategist",
      "tagline": "Don't let your dreams be dreams",
      "location": "Chicago, IL",
      "created_at": "2026-06-05T13:28:13.806Z",
      "updated_at": "2026-06-10T13:03:50.424Z",
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
    "content_excerpt": "Hey guys,\n\nWe won the Leto account! This is huge for us, it really marks a turning point for the company.\n\nAs you know we've been pursuing bigger clients in the consumer space, but we've done so carefully. We've never been about getting the biggest clients - those are easy to get. We've been tryi...",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479842/subscription.json",
    "attachments_sample": [],
    "previewable_attachments": [],
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/messages/1069479842",
    "unread_url": "https://3.basecampapi.com/195539477/my/unreads/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1708f8c9adb5dd70ebcc6837a0c054bacaf792fe.json",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1708f8c9adb5dd70ebcc6837a0c054bacaf792fe.json",
    "memory_url": "https://3.basecampapi.com/195539477/my/readings/20/memory.json",
    "bubble_up_url": "https://3.basecampapi.com/195539477/my/readings/20/bubble_up.json",
    "subscribed": true
  },
  {
    "id": 23,
    "created_at": "2026-06-10T13:07:28.573Z",
    "updated_at": "2026-06-10T13:07:28.580Z",
    "section": "bubbles",
    "unread_count": 0,
    "unread_at": null,
    "read_at": "2026-06-10T13:07:28.580Z",
    "readable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg2Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--929b3637d6257a5132a133447583416ac5fa7db4",
    "readable_identifier": "Z2lkOi8vYmMzL1JlY29yZGluZy8xMDY5NDc5ODYy",
    "title": "Kickoff: The Leto Microsite!",
    "type": "Message",
    "icon_type": "message",
    "bucket_name": "The Leto Laptop",
    "creator": {
      "id": 1049715938,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--4ccc567a0a3b10e354bca909b704637b601f0b16",
      "name": "Annie Bryan",
      "email_address": "annie@honchodesign.com",
      "personable_type": "User",
      "title": "Central Markets Manager",
      "tagline": "To open a store is easy, to keep it open is an art",
      "location": null,
      "created_at": "2026-06-05T13:28:17.050Z",
      "updated_at": "2026-06-05T13:28:17.050Z",
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
    "content_excerpt": "Hey guys,\n\nWelcome to the project, excited to get going! I'll be managing this, the first project, with Jay as the lead on the account overall.\n\nThere are a lot of components to the account overall, and this is just the first of many. This microsite will serve as a teaser to Leto's newest product...",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479862/subscription.json",
    "attachments_sample": [],
    "previewable_attachments": [],
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/messages/1069479862",
    "unread_url": "https://3.basecampapi.com/195539477/my/unreads/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg2Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--929b3637d6257a5132a133447583416ac5fa7db4.json",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg2Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--929b3637d6257a5132a133447583416ac5fa7db4.json",
    "memory_url": "https://3.basecampapi.com/195539477/my/readings/23/memory.json",
    "bubble_up_url": "https://3.basecampapi.com/195539477/my/readings/23/bubble_up.json",
    "bubble_up_at": "2026-06-15T13:00:00.000Z",
    "subscribed": false
  }
]
```
<!-- END GET /my/readings/bubble_ups.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/readings/bubble_ups.json
```

To paginate through bubble-ups:

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/readings/bubble_ups.json?page=2
```


Mark as read
------------

* `PUT /my/unreads.json` will mark the specified items as read.

**Required parameters**:

* `readables` - an array of `readable_sgid` values from the notifications response. These identify the items to mark as read.

Returns `200 OK` on success with no body.

###### Example JSON Request

```json
{
  "readables": [
    "BAh7BkkiC19yYWlscwY6BkVU...",
    "BAh7BkkiC19yYWlscwY6BkVU..."
  ]
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -X PUT \
  -d '{ "readables": ["BAh7BkkiC19yYWlscwY6BkVU..."] }' \
  https://3.basecampapi.com/$ACCOUNT_ID/my/unreads.json
```

[1]: people.md#people
[pagination]: ../README.md#pagination
