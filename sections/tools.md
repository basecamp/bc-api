Tools
=====

Tools are the features available in a project's dock. Every project has a dock containing tools like Message Board, To-dos, Docs & Files, Campfire, Schedule, etc. You can get, create, rename, reposition, and remove tools.

To find a project's tools, see the `dock` array in the [Get a project][project] response. Each dock entry includes the tool's `id`, `name`, `title`, `enabled` status, and `position`.

Endpoints:

- [Get a tool](#get-a-tool)
- [Create a tool](#create-a-tool)
- [Update a tool](#update-a-tool)
- [Enable a tool](#enable-a-tool)
- [Reposition a tool](#reposition-a-tool)
- [Disable a tool](#disable-a-tool)
- [Trash a tool](#trash-a-tool)

Get a tool
----------

* `GET /dock/tools/2.json` will return the tool with ID `2`.

###### Example JSON Response
<!-- START GET /dock/tools/2.json -->
```json
{
  "id": 1069479832,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-28T17:23:17.384Z",
  "updated_at": "2026-07-21T00:01:05.529Z",
  "title": "Chat",
  "inherits_status": true,
  "type": "Chat::Transcript",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/chats/1069479832.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/chats/1069479832",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgzMj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--7e5f099cbaea13ac831cef8c56f500ab58170a86.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479832/subscription.json",
  "position": 5,
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
    "updated_at": "2026-07-21T01:06:02.483Z",
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
```
<!-- END GET /dock/tools/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/dock/tools/2.json
```


Create a tool
-------------

* `POST /buckets/1/dock/tools.json` adds a tool of a given type to the dock of the project with ID `1`.

**Required parameters**:
* `tool_type` - the kind of tool to add. One of `Message::Board`, `Todoset`, `Vault`, `Schedule`, `Chat::Transcript`, `Kanban::Board`, `Questionnaire`, or `Inbox`.

_Optional parameters_:
* `title` - the name for the tool. When omitted, Basecamp chooses the title.
* `visible_to_clients` - a top-level boolean controlling [client visibility][client_visibility]. It only takes effect for the tool types that manage their own visibility — `Chat::Transcript` and `Kanban::Board` — which otherwise start hidden from clients; pass `true` to create one already visible. All other tool types inherit the project's default and ignore this parameter. It applies only when a **new** tool is created; re-enabling an existing tool keeps its current visibility.

This endpoint will return `201 Created` with the JSON representation of the tool if successful. The response body matches [Get a tool](#get-a-tool).

###### Example JSON Request

```json
{
  "tool_type": "Chat::Transcript",
  "title": "Q&A Chat",
  "visible_to_clients": true
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"tool_type":"Chat::Transcript","title":"Q&A Chat","visible_to_clients":true}' \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/dock/tools.json
```


Update a tool
-------------

* `PUT /dock/tools/2.json` allows renaming the tool with ID `2`.

**Required parameters**: `title` for the new name.

This endpoint will return `200 OK` with the updated JSON representation of the tool.

###### Example JSON Request

```json
{
  "title": "Team Chat"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"title":"Team Chat"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/dock/tools/2.json
```


Enable a tool
-------------

* `POST /buckets/1/recordings/2/position.json` enables the tool with recording ID `2` in the project with ID `1`, adding it to the dock.

No parameters required. The tool will be positioned at the end of the dock.

This endpoint will return `201 Created` if successful.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/recordings/2/position.json
```


Reposition a tool
-----------------

* `PUT /buckets/1/recordings/2/position.json` changes the position of the tool with recording ID `2` in the project with ID `1`.

**Required parameters**: `position` - the new position (1-based index).

This endpoint will return `200 OK` if successful.

###### Example JSON Request

```json
{
  "position": 1
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"position":1}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/recordings/2/position.json
```


Disable a tool
--------------

* `DELETE /buckets/1/recordings/2/position.json` disables the tool with recording ID `2` in the project with ID `1`, removing it from the dock.

The tool is not deleted - it's just hidden from the dock. It can be re-enabled using the [Enable a tool](#enable-a-tool) endpoint.

This endpoint will return `204 No Content` if successful.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/recordings/2/position.json
```


Trash a tool
------------

* `DELETE /dock/tools/2.json` trashes the tool with ID `2`.

This permanently removes the tool and all its content. Use with caution.

This endpoint will return `204 No Content` if successful.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/dock/tools/2.json
```


Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/dock/tools/2.json` → [Get a tool](#get-a-tool)
* `PUT /buckets/1/dock/tools/2.json` → [Update a tool](#update-a-tool)
* `DELETE /buckets/1/dock/tools/2.json` → [Trash a tool](#trash-a-tool)

[project]: projects.md#get-a-project
[client_visibility]: client_visibility.md
