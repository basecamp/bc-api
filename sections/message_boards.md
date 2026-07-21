Message Boards
==============

All messages under a project are children of a Message Board resource.

Endpoints:

- [Get message board](#get-message-board)


Get message board
-----------------

* `GET /message_boards/2.json` will return the message board with an ID of `2`.

To get the message board ID for a project, see the [Get a project][1] endpoint's `dock` payload. To retrieve its messages, see the [Get messages][2] endpoint.

###### Example JSON Response
<!-- START GET /message_boards/2.json -->
```json
{
  "id": 1069479828,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-28T17:23:17.306Z",
  "updated_at": "2026-07-21T01:05:57.487Z",
  "title": "Message Board",
  "inherits_status": true,
  "type": "Message::Board",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/message_boards/1069479828.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/message_boards/1069479828",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgyOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--e9ad500b82827907ba0071a983b037a83c60b289.json",
  "position": 1,
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
  "messages_count": 9,
  "messages_url": "https://3.basecampapi.com/195539477/buckets/2085958505/message_boards/1069479828/messages.json",
  "app_messages_url": "https://3.basecamp.com/195539477/buckets/2085958505/message_boards/1069479828/messages"
}
```
<!-- END GET /message_boards/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/message_boards/2.json
```



Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/message_boards/2.json` → [Get message board](#get-message-board)

[1]: projects.md#get-a-project
[2]: messages.md#get-messages
[3]: recordings.md#trash-a-recording
