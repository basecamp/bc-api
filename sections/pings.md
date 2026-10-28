Pings
=====

Endpoints:

- [Get Pings](#get-pings)
- [Get a Ping](#get-a-ping)
- [Create a Ping](#create-a-ping)

A Ping is a private conversation between people on the same account, not tied to a project. A Ping with two people (you and one other) is a direct Ping. A Ping with more than two is a group Ping. Each Ping has one Campfire, and its messages are the lines in that Campfire. See [Reading and writing lines in a Ping](#reading-and-writing-lines-in-a-ping).

In the API a Ping is a Circle. Its endpoints live under `/circles`, its ID is the ID of its bucket, and anything recorded in it, like a Campfire line in a search result or the [event feed](event_feed.md), has a `bucket` of type `Circle`.

A company can turn Pings off. For people at that company, every endpoint here answers `403 Forbidden` with `{ "error": "Pings have been disabled" }`.

[Agents](../README.md#agents-calling-the-api-as-themselves) can use these endpoints. They see only the Pings they are in, and a Ping they create must include at least one person who can use Pings. Creating a Ping needs a token with `full` scope. An agent is refused lines in an archived Ping with `agent_not_permitted`.

Get Pings
---------

* `GET /circles.json` will return the active Pings the current user is in, most recently updated first.

A Ping appears here once someone has posted a line in it. A Ping you have just created, with nothing said yet, isn't listed, but you already have it from the [create response](#create-a-ping). Archived Pings aren't listed either, though [Get a Ping](#get-a-ping) still returns them.

The list is not paginated: every active Ping comes back in one response, with no `Link` or `X-Total-Count` header. It does support [HTTP caching](../README.md#using-http-caching).

###### Example JSON Response
<!-- START GET /circles.json -->
```json
[
  {
    "id": 2085958506,
    "created_at": "2026-10-19T15:15:25.688Z",
    "updated_at": "2026-10-19T15:15:25.771Z",
    "title": "Annie Bryan",
    "named": false,
    "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOJkkT4=--732a71fbd28ec10d9bf4466abd3588a8bea40bdb/avatar",
    "url": "https://3.basecampapi.com/195539477/circles/2085958506.json",
    "app_url": "https://3.basecamp.com/195539477/circles/2085958506",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwNj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--c1f4e47bbc088a5055d422c816957a763ed42aec.json",
    "room_url": "https://3.basecampapi.com/195539477/buckets/2085958506/chats/1069480162.json",
    "links": {
      "self": "https://3.basecampapi.com/195539477/circles/2085958506.json",
      "app": "https://3.basecamp.com/195539477/circles/2085958506",
      "bookmark": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwNj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--c1f4e47bbc088a5055d422c816957a763ed42aec.json",
      "lines": "https://3.basecampapi.com/195539477/buckets/2085958506/chats/1069480162/lines.json",
      "files": "https://3.basecampapi.com/195539477/buckets/2085958506/chats/1069480162/uploads.json"
    },
    "people": [
      {
        "id": 1049715938,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--4ccc567a0a3b10e354bca909b704637b601f0b16",
        "name": "Annie Bryan",
        "personable_type": "User",
        "title": "Central Markets Manager",
        "tagline": "To open a store is easy, to keep it open is an art",
        "location": null,
        "created_at": "2026-10-19T15:14:26.185Z",
        "updated_at": "2026-10-19T15:14:26.185Z",
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
      }
    ]
  }
]
```
<!-- END GET /circles.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/circles.json
```

Get a Ping
----------

* `GET /circles/2.json` will return the Ping with ID `2`, if the current user is in it.

The `id` is the Ping's own ID, not its Campfire's. A Ping the current user isn't in answers `404 Not Found`.

The response has these fields beyond the usual `id`, `created_at` and `updated_at`:

* `title` - the name to show for the Ping: the group's name if it has one, otherwise the other people's names.
* `named` - whether the title was set by a person, rather than built from the people in the Ping.
* `people` - the other people in the Ping, as [full person objects](../README.md#people-not-users). It leaves out the current user, unless they are the only one in the Ping.
* `links` - the URLs to follow: `self`, `app` (the Ping in the Basecamp web app), `bookmark`, `lines` (the Ping's Campfire lines) and `files` (its Campfire uploads). A group Ping with more than one other person also has `edit_title`, a web app page, not an API endpoint.
* `room_url` - the URL of the Ping's Campfire. Follow `links.lines` and `links.files` rather than building URLs from it.
* `image_url` - only present when a group Ping has a custom image.

###### Example JSON Response
<!-- START GET /circles/2.json -->
```json
{
  "id": 2085958506,
  "created_at": "2026-10-19T15:15:25.688Z",
  "updated_at": "2026-10-19T15:15:25.771Z",
  "title": "Annie Bryan",
  "named": false,
  "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOJkkT4=--732a71fbd28ec10d9bf4466abd3588a8bea40bdb/avatar",
  "url": "https://3.basecampapi.com/195539477/circles/2085958506.json",
  "app_url": "https://3.basecamp.com/195539477/circles/2085958506",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwNj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--c1f4e47bbc088a5055d422c816957a763ed42aec.json",
  "room_url": "https://3.basecampapi.com/195539477/buckets/2085958506/chats/1069480162.json",
  "links": {
    "self": "https://3.basecampapi.com/195539477/circles/2085958506.json",
    "app": "https://3.basecamp.com/195539477/circles/2085958506",
    "bookmark": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwNj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--c1f4e47bbc088a5055d422c816957a763ed42aec.json",
    "lines": "https://3.basecampapi.com/195539477/buckets/2085958506/chats/1069480162/lines.json",
    "files": "https://3.basecampapi.com/195539477/buckets/2085958506/chats/1069480162/uploads.json"
  },
  "people": [
    {
      "id": 1049715938,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--4ccc567a0a3b10e354bca909b704637b601f0b16",
      "name": "Annie Bryan",
      "personable_type": "User",
      "title": "Central Markets Manager",
      "tagline": "To open a store is easy, to keep it open is an art",
      "location": null,
      "created_at": "2026-10-19T15:14:26.185Z",
      "updated_at": "2026-10-19T15:14:26.185Z",
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
    }
  ]
}
```
<!-- END GET /circles/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/circles/2.json
```

Create a Ping
-------------

* `POST /circles.json` will open a Ping with the given people, and add the current user.

The response is `201 Created` with the Ping, in the same shape as [Get a Ping](#get-a-ping). It is also `201 Created` when the Ping already existed: an active direct Ping between the same two people is reused, and so is an active group Ping with the same members, unless you set `new_group`. An archived Ping is never reused; the request opens a new one.

**Required parameters**: the people to ping, as either

* `user_ids` - an array of person IDs. Take them from [Get pingable people](people.md#get-pingable-people).
* `users` - the same IDs as a comma-separated string. Used only when `user_ids` is missing or an empty array.

The IDs may also be sent inside a `circle` object, as `{ "circle": { "user_ids": [ 1, 2 ] } }`. IDs of people the current user can't reach, or who aren't on the account, are dropped, not rejected, so check `people` in the response. You don't list yourself; you are always added, so a list of IDs that are all unreachable opens a Ping with only yourself (an agent gets `422` instead, see below).

_Optional parameters_:

* `new_group` - set to `true` to start a new group Ping even when a group Ping with exactly these members already exists. Direct Pings are unaffected: two people only ever share one active direct Ping.

Errors:

* `400 Bad Request` if neither a non-empty `user_ids` nor a non-blank `users` is given. An empty `user_ids` array alone is rejected too.
* `403 Forbidden` if Pings are turned off for the current user.
* `422 Unprocessable Entity`, with no body, if the Ping would have no person in it who can use Pings. This only happens to agents, which can't start a Ping with only other agents.

###### Example JSON Request

```json
{
  "user_ids": [ 1049715944 ]
}
```

###### Example JSON Response
<!-- START POST /circles.json -->
```json
{
  "id": 2085958507,
  "created_at": "2026-10-19T15:15:26.805Z",
  "updated_at": "2026-10-19T15:15:26.871Z",
  "title": "Steve Marsh",
  "named": false,
  "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOhkkT4=--b169e35b345bcc26eca6964b7ef7de2c16b6f238/avatar",
  "url": "https://3.basecampapi.com/195539477/circles/2085958507.json",
  "app_url": "https://3.basecamp.com/195539477/circles/2085958507",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwNz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--255d5e86fdeb49464962b27ec80fee5cf1153f5f.json",
  "room_url": "https://3.basecampapi.com/195539477/buckets/2085958507/chats/1069480165.json",
  "links": {
    "self": "https://3.basecampapi.com/195539477/circles/2085958507.json",
    "app": "https://3.basecamp.com/195539477/circles/2085958507",
    "bookmark": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9CdWNrZXQvMjA4NTk1ODUwNz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--255d5e86fdeb49464962b27ec80fee5cf1153f5f.json",
    "lines": "https://3.basecampapi.com/195539477/buckets/2085958507/chats/1069480165/lines.json",
    "files": "https://3.basecampapi.com/195539477/buckets/2085958507/chats/1069480165/uploads.json"
  },
  "people": [
    {
      "id": 1049715944,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk0ND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--5c49e7f857f7a2aea319ae399f8b00eb63123ef9",
      "name": "Steve Marsh",
      "personable_type": "User",
      "title": "Legacy Directives Strategist",
      "tagline": "You can do it!",
      "location": null,
      "created_at": "2026-10-19T15:14:27.315Z",
      "updated_at": "2026-10-19T15:14:27.315Z",
      "email_address": "steve@honchodesign.com",
      "bio": "You can do it!",
      "admin": false,
      "owner": false,
      "client": false,
      "employee": true,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOhkkT4=--b169e35b345bcc26eca6964b7ef7de2c16b6f238/avatar",
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
  ]
}
```
<!-- END POST /circles.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -H 'Content-Type: application/json' \
  -d '{ "user_ids": [ 1049715944 ] }' \
  https://3.basecampapi.com/$ACCOUNT_ID/circles.json
```

Reading and writing lines in a Ping
-----------------------------------

A Ping's messages are the lines in its Campfire. Use the Ping's `links.lines` URL with the [Campfire line endpoints](campfires.md#get-campfire-lines):

* `GET` the `links.lines` URL to [read the lines](campfires.md#get-campfire-lines), which are [paginated][pagination].
* `POST` to it to [post a line](campfires.md#create-a-campfire-line). People in the Ping are notified as for any Ping, and the line makes the Ping appear in [Get Pings](#get-pings).
* `links.files` takes [Campfire uploads](campfires.md#upload-a-file-to-a-campfire) the same way.

The Campfire's ID is the last number in `links.lines`, so the flat routes work too: for `.../buckets/1/chats/2/lines.json`, use `/chats/2/lines.json` with the Campfire endpoints.

A Ping's Campfire isn't returned by [Get Campfires](campfires.md#get-campfires), and `GET /chats/2.json` on one answers `302 Found`, redirecting to the Ping at `/circles/{id}` on the same API host, without `.json`; the redirect target answers JSON to a client that accepts it. Use [Get a Ping](#get-a-ping) for the Ping itself.

The generic [recording](recordings.md) endpoints read a Ping's Campfire and its lines, but don't change them. Trashing, archiving or unarchiving one, changing its title or client visibility, publishing it, and [updating its subscription](subscriptions.md#update-subscription) answer `403 Forbidden`, to everyone in the Ping, agents included. What you do for yourself still works: [subscribing](subscriptions.md#subscribe-current-user) and [unsubscribing](subscriptions.md#unsubscribe-current-user) yourself, [bookmarking](my_bookmarks.md#create-a-bookmark) the Ping, and bubbling up a line. [Boost](boosts.md#create-a-boost) a line as in any Campfire, and edit or delete one with the [Campfire line endpoints](campfires.md#update-a-campfire-line).

[pagination]: ../README.md#pagination
