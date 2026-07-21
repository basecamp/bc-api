Webhooks
========

Basecamp can notify your application through webhooks when something is changed.
A webhook consists of a payload URL to be called, which must be HTTPS, and a list of types that'll trigger calls.

Basecamp will attempt to call the payload URL up to 10 times before deactivating the webhook. The duration between attempts
will grow exponentially longer to give your service time to recover. Basecamp will only consider a HTTP status code in
the 2xx range to be a successful response. We will not follow a 3xx redirect.

A webhook can be subscribed to updates from the types detailed below. The default is to subscribe to all of them.

Endpoints:

- Comment
- Client::Approval::Response
- Client::Forward
- Client::Reply
- CloudFile
- Document
- GoogleDocument
- Inbox::Forward
- Kanban::Card
- Kanban::Step
- Message
- Question
- Question::Answer
- Schedule::Entry
- Todo
- Todolist
- Upload
- Vault

Note that chat isn't amongst the options. Check our [chat bot API][1] for that. Also, `CloudFile` type corresponds to files linked from any cloud provider different from Google Drive (which has its separate `GoogleDocument` type). 

Whenever an event is created for any of the types that webhook was created to match, Basecamp will call your payload URL.
All payloads follow the same JSON format:

```json
{
  "id": 9007199254741210,
  "kind": "message_created",
  "details": { "notified_recipient_ids": [1007299144] },
  "created_at": "2016-06-08T19:00:41.933Z",
  "recording": {
    "id": 9007199254741622,
    "status": "active",
    "created_at": "2016-07-20T00:21:41.446Z",
    "updated_at": "2016-07-19T21:29:08.739Z",
    "title": "Welcome to Basecamp!",
    "inherits_status": true,
    "type": "Message",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958498/messages/9007199254741622.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958498/messages/9007199254741622",
    "comments_count": 1,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958498/recordings/9007199254741622/comments.json",
    "parent": {
      "id": 9007199254741434,
      "title": "Message Board",
      "type": "Message::Board",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958498/message_boards/9007199254741434.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958498/message_boards/9007199254741434"
    },
    "bucket": {
      "id": 2085958498,
      "name": "The Leto Laptop",
      "type": "Project"
    },
    "creator": {
      "id": 1007299165,
      "attachable_sgid": "BAh7CEkiCGdpZAY6BkVUSSIrZ2lkOi8vYmMzL1BlcnNvbi8xMDA3Mjk5MTY1P2V4cGlyZXNfaW4GOwBUSSIMcHVycG9zZQY7AFRJIg9hdHRhY2hhYmxlBjsAVEkiD2V4cGlyZXNfYXQGOwBUMA==--c28a27d0c490353fc1a5c2a50ce8eda0fae07370",
      "name": "Matt Donahue",
      "email_address": "matt@honchodesign.com",
      "personable_type": "User",
      "title": "Global Data Strategist",
      "bio": null,
      "created_at": "2016-07-19T21:27:47.654Z",
      "updated_at": "2016-07-19T21:27:47.654Z",
      "admin": false,
      "owner": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecamp-static.com/195539477/people/BAhpBF0qCjw=--21513efb0cf6f64f7a0720b2c56ac6145ae6680c/avatar-64-x4"
    },
    "content": "<div>Hey all, here are some high res shots of the laptop hardware that we can use. These are not public yet, so be careful with how you share them. We don't want any leaks at all with these images.</div>"
  },
  "creator": {
    "id": 1007299165,
    "attachable_sgid": "BAh7CEkiCGdpZAY6BkVUSSIrZ2lkOi8vYmMzL1BlcnNvbi8xMDA3Mjk5MTY1P2V4cGlyZXNfaW4GOwBUSSIMcHVycG9zZQY7AFRJIg9hdHRhY2hhYmxlBjsAVEkiD2V4cGlyZXNfYXQGOwBUMA==--c28a27d0c490353fc1a5c2a50ce8eda0fae07370",
    "name": "Matt Donahue",
    "email_address": "matt@honchodesign.com",
    "personable_type": "User",
    "title": "Global Data Strategist",
    "bio": null,
    "created_at": "2016-07-19T21:27:47.654Z",
    "updated_at": "2016-07-19T21:27:47.654Z",
    "admin": false,
    "owner": false,
    "time_zone": "America/Chicago",
    "avatar_url": "https://3.basecamp-static.com/195539477/people/BAhpBF0qCjw=--21513efb0cf6f64f7a0720b2c56ac6145ae6680c/avatar-64-x4"
  }
}
```

As you'll note, the recording format is the basic generic format that all other content endpoints share, with the addition of a `content` field. This format won't include as many details about the recording as other specific endpoints return. For example, for a [todo][2], this won't include fields such as `description`, `completed` or `assignees`.

The payload for copy/move events will also include some details on the copied recording under `"copy"`. For example:
```json
{
   "id":1479523571,
   "kind":"todo_copied",
   "details":{
      "copy_id":981721240
   },
   "created_at":"2018-03-23T10:19:33.908+01:00",
   "copy":{
      "id":981721240,
      "url":"https://3.basecampapi.com/195539477/buckets/2085958499/todos/981721240.json",
      "app_url":"https://3.basecamp.com/195539477/buckets/2085958499/todos/981721240",
      "bucket":{
         "id":2085958499,
      }
   },
   "recording":{
      "id":968814335,
      "status":"active",
      "created_at":"2018-03-16T12:17:04.938+01:00",
      "updated_at":"2018-03-19T09:31:12.753+01:00",
      "title":"Go cutting edge: iOS8 and Android 4.5 only",
      "inherits_status": true,
      "type":"Todo",
      "url":"https://3.basecampapi.com/195539477/buckets/68833643212/todos/968814335.json",
      "app_url":"https://3.basecamp.com/195539477/buckets/68833643212/todos/968814335",
      "bookmark_url":"https://3.basecampapi.com/195539477/my/bookmarks/BAh7CEkiCGdpZAY6BkVUSSItZ2lkOi8vYmMzL1JlY29yZGluZy85Njg4MTQzMzU_ZXhwaXJlc19pbgY7AFRJIgxwdXJwb3NlBjsAVEkiDXJlYWRhYmxlBjsAVEkiD2V4cGlyZXNfYXQGOwBUMA==--9c496c78316f7ff7c52fbbbc957f198efd1c338c.json",
      "parent":{
         "id":968814030,
         "title": "Strategy ideas",
         "type":"Todolist",
         "url":"https://3.basecampapi.com/195539477/buckets/68833643212/todolists/968814030.json",
         "app_url":"https://3.basecamp.com/195539477/buckets/68833643212/todolists/968814030"
      },
      "bucket":{
         "id":68833643212,
         "name":"The Leto Laptop",
         "type":"Project"
      },
      "creator": {
        "id": 1049715915,
        "attachable_sgid": "BAh7CEkiCGdpZAY6BkVUSSIrZ2lkOi8vYmMzL1BlcnNvbi8xMDQ5NzE1OTE1P2V4cGlyZXNfaW4GOwBUSSIMcHVycG9zZQY7AFRJIg9hdHRhY2hhYmxlBjsAVEkiD2V4cGlyZXNfYXQGOwBUMA==--5f103c46d4f123f0068fcd0192a0f7fea7f26193",
        "name": "Annie Bryan",
        "email_address": "annie@honchodesign.com",
        "personable_type": "User",
        "title": "Central Markets Manager",
        "bio": "To open a store is easy, to keep it open is an art",
        "created_at": "2018-02-14T17:02:25.043Z",
        "updated_at": "2018-02-14T17:02:25.043Z",
        "admin": false,
        "owner": false,
        "time_zone": "America/Chicago",
        "avatar_url": "https://3.basecamp-static.com/195539477/people/BAhpBMtkkT4=--e609ef146e39f9ca5e4bb7242fdfd50aec4c3b3f/avatar-64-x4",
        "company": {
          "id": 1033447817,
          "name": "Honcho Design"
        }
      },
      "content":"Go cutting edge: iOS8 and Android 4.5 only"
   },
  "creator": {
    "id": 1049715915,
    "attachable_sgid": "BAh7CEkiCGdpZAY6BkVUSSIrZ2lkOi8vYmMzL1BlcnNvbi8xMDQ5NzE1OTE1P2V4cGlyZXNfaW4GOwBUSSIMcHVycG9zZQY7AFRJIg9hdHRhY2hhYmxlBjsAVEkiD2V4cGlyZXNfYXQGOwBUMA==--5f103c46d4f123f0068fcd0192a0f7fea7f26193",
    "name": "Annie Bryan",
    "email_address": "annie@honchodesign.com",
    "personable_type": "User",
    "title": "Central Markets Manager",
    "bio": "To open a store is easy, to keep it open is an art",
    "created_at": "2018-02-14T17:02:25.043Z",
    "updated_at": "2018-02-14T17:02:25.043Z",
    "admin": false,
    "owner": false,
    "time_zone": "America/Chicago",
    "avatar_url": "https://3.basecamp-static.com/195539477/people/BAhpBMtkkT4=--e609ef146e39f9ca5e4bb7242fdfd50aec4c3b3f/avatar-64-x4",
    "company": {
      "id": 1033447817,
      "name": "Honcho Design"
    }
  }
}
```

After sending the payload, Basecamp will record the interaction with your application as a delivery record that can be introspected for debugging.
The delivery record includes the full request and response that occurred for that specific event relay.

##### Events triggering webhooks

Basecamp will send the following lifecycle events for all types, here using message as an example:

- message_created / message_active
- message_title_updated / message_content_updated
- message_copied / message_inserted
- message_archived / message_unarchived
- message_trashed / message_untrashed
- message_deleted

There are also a handful of shared operations around the types that pertain to all types, again using message as an example:

- message_subscribers_changed
- message_publicized

Comments added on any recording will trigger the following event:

- comment_created

Additionally, some types have unique events. They are as follows:

Todos:

- todo_completed
- todo_uncompleted

Questions:

- question_paused
- question_resumed

Assignable types (Todo, Kanban::Card, and Kanban::Step) emit an event whenever their assignees change:

- todo_assignment_changed
- kanban_card_assignment_changed
- kanban_step_assignment_changed

The `details` of an assignment event list the people added and removed:

```json
{
  "kind": "kanban_card_assignment_changed",
  "details": {
    "added_person_ids": [ 1049715939 ],
    "removed_person_ids": [ 1049715913 ]
  }
}
```

###### Status propagation to children recordings

Starting the 1st of July 2024, Basecamp won't notify of changes that are automatically propagated to children's recordings. For example, when archiving a todolist, all its contained todos and comments within each todo will get archived too. In this case, Basecamp will only notify the status change on the parent todolist, not on each of the contained items.

###### Endpoints

- [Get webhooks](#get-webhooks)
- [Get a webhook](#get-a-webhook)
- [Create a webhook](#create-a-webhook)
- [Update a webhook](#update-a-webhook)
- [Destroy a webhook](#destroy-a-webhook)

**Note:** client users aren't allowed to perform any of the webhook related actions, so calling these endpoints while being authenticated with a client user will get a `403 Forbidden` response. 

Get webhooks
------------

* `GET /buckets/1/webhooks.json` will return all the webhooks for the project with an ID of `1`.

###### Example JSON Response
<!-- START GET /buckets/1/webhooks.json -->
```json
[
  {
    "id": 1051369971,
    "active": true,
    "created_at": "2026-05-28T17:29:05.487Z",
    "updated_at": "2026-05-28T17:29:05.487Z",
    "payload_url": "https://example.com/endpoint",
    "types": [
      "all"
    ],
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/webhooks/1051369971.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/webhooks/1051369971"
  }
]
```
<!-- END GET /buckets/1/webhooks.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/webhooks.json
```

Get a webhook
-------------

* `GET /webhooks/3.json` will return the webhook with an ID of `3`.

The recent deliveries array contains up to the 25 most recent delivery exchanges, sorted with the most recent first. It's empty when the webhook hasn't delivered anything yet.

###### Example JSON Response
<!-- START GET /webhooks/3.json -->
```json
{
  "id": 1051369971,
  "active": true,
  "created_at": "2026-05-28T17:29:05.487Z",
  "updated_at": "2026-05-28T17:29:05.487Z",
  "payload_url": "https://example.com/endpoint",
  "types": [
    "all"
  ],
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/webhooks/1051369971.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/webhooks/1051369971",
  "recent_deliveries": [
    {
      "id": 627138775,
      "created_at": "2026-07-21T01:05:31.186Z",
      "request": {
        "headers": {
          "Content-Type": "application/json",
          "User-Agent": "Basecamp3 Webhook",
          "X-Request-Id": "3845f9bd-2b8a-4c08-9f30-c01135ab2f23"
        },
        "body": {
          "id": 1052473966,
          "kind": "todo_completed",
          "details": {
            "notified_recipient_ids": []
          },
          "created_at": "2026-07-20T20:05:29.832-05:00",
          "recording": {
            "id": 1069480405,
            "status": "active",
            "visible_to_clients": false,
            "created_at": "2026-07-20T20:05:28.858-05:00",
            "updated_at": "2026-07-20T20:05:29.822-05:00",
            "title": "Confirm the launch-party caterer",
            "inherits_status": true,
            "type": "Todo",
            "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todos/1069480405.json",
            "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todos/1069480405",
            "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDQwNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1bd5883b4c5a15564fbe2c41278cb646dddead47.json",
            "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480405/subscription.json",
            "parent": {
              "id": 1069479863,
              "title": "Background and research",
              "type": "Todolist",
              "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479863.json",
              "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479863"
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
              "created_at": "2026-05-28T12:22:22.069-05:00",
              "updated_at": "2026-07-20T19:05:55.167-05:00",
              "email_address": "victor@honchodesign.com",
              "bio": "Don't let your dreams be dreams",
              "admin": true,
              "owner": true,
              "client": false,
              "employee": true,
              "time_zone": "America/Chicago",
              "avatar_url": "https://bc3-production-assets-cdn.basecamp-static.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
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
            "content": "Confirm the launch-party caterer"
          },
          "creator": {
            "id": 1049715913,
            "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
            "name": "Victor Cooper",
            "personable_type": "User",
            "title": "Chief Strategist",
            "tagline": "Don't let your dreams be dreams",
            "location": "Chicago, IL",
            "created_at": "2026-05-28T12:22:22.069-05:00",
            "updated_at": "2026-07-20T19:05:55.167-05:00",
            "email_address": "victor@honchodesign.com",
            "bio": "Don't let your dreams be dreams",
            "admin": true,
            "owner": true,
            "client": false,
            "employee": true,
            "time_zone": "America/Chicago",
            "avatar_url": "https://bc3-production-assets-cdn.basecamp-static.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
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
      },
      "response": {
        "headers": {
          "Content-Type": "application/json"
        },
        "code": 200,
        "message": "OK",
        "body": "{}"
      }
    }
  ]
}
```
<!-- END GET /webhooks/3.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/webhooks/3.json
```

Create a webhook
----------------

* `POST /buckets/1/webhooks.json` creates a webhook in the project with an ID of `1`.

**Required parameters**: `payload_url` for the HTTPS url that Basecamp should call.
_Optional parameters_: `types` as an array of types, options given in the introduction.

This endpoint will return `201 Created` with the current JSON representation of the webhook if the creation was a success. See the [Get a webhook](#get-a-webhook) endpoint for more info on the payload.

This endpoint will return `400 Bad Request` if the payload URL is not a valid HTTPS URL or other validation errors occur. It will return `507 Insufficient Storage` if the account has reached its webhook limit.

###### Example JSON Request

```json
{
  "payload_url": "https://example.com/endpoint",
  "types": [ "Todo", "Todolist" ]
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"payload_url":"https://example.com/endpoint","types":["Todo","Todolist"]}' \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/webhooks.json
```

Update a webhook
----------------

* `PUT /webhooks/3.json` allows changing the payload url and types of the webhook with an ID of `3`.

**Required parameters**: `payload_url` for the HTTPS url that Basecamp will call.
_Optional parameters_: `types` as an array of types, options given in the introduction. `active` as a boolean whether this webhook should be matching.

This endpoint will return `200 OK` with the current JSON representation of the webhook if the update was a success. See the [Get a webhook](#get-a-webhook) endpoint for more info on the payload.

This endpoint will return `400 Bad Request` if the payload URL is not a valid HTTPS URL or other validation errors occur.

###### Example JSON Request

```json
{
  "payload_url": "https://example.com/endpoint",
  "types": ["Todo", "Todolist"],
  "active": true
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"payload_url":"https://example.com/endpoint","types":["Todo","Todolist"],"active":true}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/webhooks/3.json
```

Destroy a webhook
-----------------

* `DELETE /webhooks/3.json` will delete the webhook with an ID of `3`.

This endpoint will return `204 No Content` if the destroy was a success.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/webhooks/3.json
```


Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/webhooks/3.json` → [Get a webhook](#get-a-webhook)
* `PUT /buckets/1/webhooks/3.json` → [Update a webhook](#update-a-webhook)
* `DELETE /buckets/1/webhooks/3.json` → [Destroy a webhook](#destroy-a-webhook)

[1]: chatbots.md
[2]: todos.md#get-a-to-do
