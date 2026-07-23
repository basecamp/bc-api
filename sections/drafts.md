Drafts
======

Endpoint for retrieving the current user's unpublished drafts across all of their active projects.

A draft is a [message](messages.md), [document](documents.md), file [upload](uploads.md), or client [approval](client_approvals.md)/[correspondence](client_correspondences.md) that has been saved but not yet published. Messages and documents can be drafted and published through the API — see the [messages](messages.md#create-a-message) and [documents](documents.md#create-a-document) sections. Uploads have their own [create](uploads.md#create-an-upload) and [update](uploads.md#update-an-upload) endpoints, but no documented way to create or publish a *draft* upload; client approvals and correspondences are read-only over the API. Drafts of all of these types still appear here, however they were authored.

Endpoints:

- [Get my drafts](#get-my-drafts)


Get my drafts
-------------

* `GET /my/drafts.json` will return a [paginated list][pagination] of the current user's drafts, most recently updated first. Drafts of every type — messages, documents, uploads, and client approvals/correspondences — are included, regardless of how they were created. Drafts whose project has been archived or trashed are excluded.

Each draft carries an `excerpt`: up to 300 characters of plain-text content, or an empty string when the draft has no body yet. `parent` is `null` for drafts filed directly under their bucket, and `scheduled_posting_at` is `null` unless the draft is scheduled to publish later.

###### Example JSON Response
<!-- START GET /my/drafts.json -->
```json
[
  {
    "id": 1069480291,
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/messages/1069480291",
    "title": "Launch announcement",
    "type": "message",
    "bucket": {
      "id": 2085958504,
      "name": "The Leto Laptop",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504"
    },
    "parent": {
      "id": 1069479829,
      "title": "Message Board",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/message_boards/1069479829"
    },
    "excerpt": "Still polishing the wording before we post this.",
    "created_at": "2026-07-22T22:11:07.611Z",
    "updated_at": "2026-07-22T22:11:07.632Z",
    "scheduled_posting_at": null
  }
]
```
<!-- END GET /my/drafts.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/drafts.json
```

[pagination]: ../README.md#pagination
