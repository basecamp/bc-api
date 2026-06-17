Search
======

Search across all content in the account that the authenticated user has access to.

Endpoints:

- [Get search metadata](#get-search-metadata)
- [Search recordings](#search-recordings)

Get search metadata
-------------------

* `GET /searches/metadata.json` returns valid filter options for search.

Use this endpoint to discover valid values for the `type` and `file_type` parameters before searching. The available types may vary, so always fetch this endpoint rather than hardcoding values.

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

Entries with `"key": null` represent the default "search everything" option. Omit the `type` or `file_type` parameter entirely to search without filtering.

Search recordings
-----------------

* `GET /search.json` will return a [paginated list][1] of recordings matching the search query.

**Required parameters**: `q` - the search query string.

_Optional parameters_:

* `type` - Filter by recording type. Use `key` values from the `recording_search_types` array returned by [Get search metadata](#get-search-metadata).
* `bucket_id` - Filter by [project][2] ID. Note: this differs from the [recordings][4] endpoint which uses `bucket`.
* `creator_id` - Filter by creator [person][3] ID.
* `file_type` - Filter attachments by type. Use `key` values from the `file_search_types` array returned by [Get search metadata](#get-search-metadata).
* `exclude_chat` - Set to `1` to exclude chat results.
* `page` - Page number for pagination (default: 1).
* `per_page` - Number of results per page (default: 50).

Results are ordered by relevance with a recency boost.

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
    "id": 1069479869,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-02-26T23:44:00.000Z",
    "updated_at": "2026-02-26T23:44:00.000Z",
    "title": "The next level",
    "inherits_status": true,
    "type": "Todolist",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958508/todolists/1069479869.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958508/todolists/1069479869",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg2OT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--e15973c9b4ad72088d0ace9758d892dd0b8714b8.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958508/recordings/1069479869/subscription.json",
    "comments_count": 0,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958508/recordings/1069479869/comments.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958508/recordings/1069479869/boosts.json",
    "position": 2,
    "parent": {
      "id": 1069479852,
      "title": "Learn the basics",
      "type": "Todoset",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958508/todosets/1069479852.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958508/todosets/1069479852"
    },
    "bucket": {
      "id": 2085958508,
      "name": "Getting Started",
      "type": "Project"
    },
    "creator": {
      "id": 1049715954,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk1ND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e48c27affa15a3d45cdcc14242ca165eedf36473",
      "name": "Basecamp",
      "email_address": null,
      "personable_type": "DummyUser",
      "title": null,
      "bio": null,
      "location": null,
      "created_at": "2026-02-26T16:46:16.078Z",
      "updated_at": "2026-02-26T16:46:16.078Z",
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBPJkkT4=--85467e2e70c9f4d94081b731e836ab4929c511d7/avatar",
      "can_ping": true,
      "can_manage_projects": false,
      "can_manage_people": false,
      "can_access_timesheet": false,
      "can_access_hill_charts": false
    },
    "description": null,
    "completed": false,
    "completed_ratio": "0/10",
    "name": "The next level",
    "color": null,
    "groups_url": "https://3.basecampapi.com/195539477/buckets/2085958508/todolists/1069479869/groups.json",
    "todos_url": "https://3.basecampapi.com/195539477/buckets/2085958508/todolists/1069479869/todos.json",
    "app_todos_url": "https://3.basecamp.com/195539477/buckets/2085958508/todolists/1069479869/todos",
    "comments_app_url": "https://3.basecamp.com/195539477/buckets/2085958508/recordings/1069479869/comments",
    "content": null,
    "plain_text_content": "Ready for more? Become a Basecamp expert!",
    "plain_text_description": "Ready for more? Become a Basecamp expert!"
  }
]
```
<!-- END GET /search.json -->

The `plain_text_content` field contains HTML with search terms wrapped in `<em>` tags for highlighting. Be sure to escape this content appropriately when rendering.

[1]: ../README.md#pagination
[2]: projects.md#projects
[3]: people.md#people
[4]: recordings.md#recordings
