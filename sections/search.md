Search
======

Search across all content in the account that the authenticated user has access to.

Endpoints:

- [Get search metadata](#get-search-metadata)
- [Search recordings](#search-recordings)

Get search metadata
-------------------

* `GET /searches/metadata.json` returns valid filter options for search.

Use this endpoint to discover valid values for the `type_names[]` and `file_type` parameters before searching. The available types may vary, so always fetch this endpoint rather than hardcoding values.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -A 'MyApp (yourname@example.com)' \
  "https://3.basecampapi.com/$ACCOUNT_ID/searches/metadata.json"
```

###### Example JSON Response
<!-- START GET /searches/metadata.json -->
```json
{
  "recording_search_types": [
    {
      "key": null,
      "value": "Everything"
    },
    {
      "key": "Kanban::Card",
      "value": "Card tables"
    },
    {
      "key": "Chat::Transcript",
      "value": "Chats"
    },
    {
      "key": "Question",
      "value": "Check-ins"
    },
    {
      "key": "Client::Correspondence",
      "value": "Client emails"
    },
    {
      "key": "Comment",
      "value": "Comments"
    },
    {
      "key": "Document",
      "value": "Documents"
    },
    {
      "key": "Schedule::Entry",
      "value": "Events"
    },
    {
      "key": "Attachment",
      "value": "Files"
    },
    {
      "key": "Vault",
      "value": "Folders"
    },
    {
      "key": "Inbox::Forward",
      "value": "Forwarded emails"
    },
    {
      "key": "Message",
      "value": "Messages"
    },
    {
      "key": "Circle",
      "value": "Pings"
    },
    {
      "key": "Todo",
      "value": "To-dos"
    }
  ],
  "file_search_types": [
    {
      "key": null,
      "value": "All files"
    },
    {
      "key": "Image",
      "value": "Images"
    },
    {
      "key": "Audio",
      "value": "Audios"
    },
    {
      "key": "Video",
      "value": "Videos"
    },
    {
      "key": "PDF",
      "value": "PDFs"
    }
  ],
  "default_creator_label": "Anyone",
  "default_bucket_label": "All projects",
  "default_circle_label": "All pings",
  "default_file_type_label": "All files",
  "default_type_label": "Everything"
}
```
<!-- END GET /searches/metadata.json -->

Entries with `"key": null` represent the default "search everything" option. Omit the `type_names[]` or `file_type` parameter entirely to search without filtering.

Search recordings
-----------------

* `GET /search.json` will return a [paginated list][1] of recordings matching the search query.

**Required parameters**: `q` - the search query string.

_Optional parameters_:

* `type_names[]` - Array of recording types to include. Use `key` values from the `recording_search_types` array returned by [Get search metadata](#get-search-metadata). Available since Basecamp 5.
* `bucket_ids[]` - Array of [project][2] IDs to filter by. Note: this differs from the [recordings][4] endpoint which uses `bucket`. Available since Basecamp 5.
* `creator_ids[]` - Array of creator [person][3] IDs to filter by. Available since Basecamp 5.
* `file_type` - Filter attachments by type. Use `key` values from the `file_search_types` array returned by [Get search metadata](#get-search-metadata).
* `exclude_chat` - Set to `1` to exclude chat results.
* `since` - Time-range filter. One of `last_7_days`, `last_30_days`, `last_90_days`, `last_12_months`, or `forever` (the default — search across all time). Unrecognized values are normalized to `forever`. Available since Basecamp 5.
* `sort` - Sort order. `best_match` (the default, also used when blank) ranks by relevance with a recency boost; `recency` orders strictly by recency, newest first. Unrecognized values fall back to recency ordering.
* `page` - Page number for pagination (default: 1).
* `per_page` - Number of results per page (default: 50).

_Deprecated parameters_ (kept for backwards compatibility with older clients; prefer the plural array forms above):

* `type` - Single recording type. Prefer `type_names[]`.
* `bucket_id` - Single [project][2] ID. Prefer `bucket_ids[]`.
* `creator_id` - Single creator [person][3] ID. Prefer `creator_ids[]`.

By default results are ordered by relevance with a recency boost. Pass `sort=recency` to order strictly by recency, newest first.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -A 'MyApp (yourname@example.com)' \
  "https://3.basecampapi.com/$ACCOUNT_ID/search.json?q=authentication"
```

###### Example JSON Response
<!-- START GET /search.json -->
```json
[
  {
    "id": 1069479842,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-04-14T21:02:00.000Z",
    "updated_at": "2026-07-21T01:05:34.577Z",
    "title": "We won Leto!",
    "inherits_status": true,
    "type": "Message",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/messages/1069479842.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069479842",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1708f8c9adb5dd70ebcc6837a0c054bacaf792fe.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479842/subscription.json",
    "comments_count": 10,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479842/comments.json",
    "boosts_count": 5,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479842/boosts.json",
    "parent": {
      "id": 1069479828,
      "title": "Message Board",
      "type": "Message::Board",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/message_boards/1069479828.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/message_boards/1069479828"
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
      "updated_at": "2026-07-21T00:05:55.167Z",
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
    "content": null,
    "content_attachments": [],
    "subject": "We won Leto!",
    "description": null,
    "plain_text_content": "Hey guys, We won the Leto account! This is huge for us, it really marks a turning point for the company. As you know we've been pursuing bigger clients in the consumer space, but we've done so carefully. We've never been about getting the biggest clients - those are easy to get. We've been trying …"
  }
]
```
<!-- END GET /search.json -->

The `plain_text_content` field contains HTML with search terms wrapped in `<em>` tags for highlighting. Be sure to escape this content appropriately when rendering.

[1]: ../README.md#pagination
[2]: projects.md#projects
[3]: people.md#people
[4]: recordings.md#recordings
