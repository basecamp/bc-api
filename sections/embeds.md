Embeds
======

An embed shows content from another site, such as a YouTube video, inline in rich text. Basecamp embeds URLs from the providers it knows, the same ones its editor offers to embed when you paste a link.

Endpoints:

- [Create an embed](#create-an-embed)
- [Get an embed](#get-an-embed)


Create an embed
---------------

* `POST /embeds.json` creates an embed for a URL, or returns the one that already exists for it.

**Required parameters**: `url` of the content to embed.

This endpoint will return `200 OK` with the embed's `sgid` in the JSON representation, whether the embed is new or Basecamp already had one for the URL. A new embed's `status` is `pending` while Basecamp asks the provider about it; [get the embed](#get-an-embed) about once a second until its `status` is `active`, or `not_found` when the provider has nothing to embed. An `active` embed has its `content_type`.

A URL no provider embeds answers `422 Unprocessable Entity` with an `error`; link to it instead. Creating more than 100 new embeds in an hour answers `429 Too Many Requests` with an `error`. Unlike other rate limits, it has no `Retry-After`: it refuses only new embeds, for the rest of the hour, so don't hold back other requests. Asking for an embed Basecamp already has still works.

###### Example JSON Request

```json
{
  "url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
}
```

###### Example JSON Response
<!-- START POST /embeds.json -->
```json
{
  "url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ",
  "status": "pending",
  "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiKmdpZDovL2JjMy9FbWJlZC8xMDMwMDk3NTAyP2V4cGlyZXNfaW4GOwBUSSIIcHVyBjsAVEkiD2F0dGFjaGFibGUGOwBU--10dcfa365b396dfbb686898681ccecb3c96dea3f"
}
```
<!-- END POST /embeds.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"url":"https://www.youtube.com/watch?v=dQw4w9WgXcQ"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/embeds.json
```


Get an embed
------------

* `GET /embeds/$SGID.json` will return the embed with the `sgid` that [creating it](#create-an-embed) returned.

###### Example JSON Response
<!-- START GET /embeds/$SGID.json -->
```json
{
  "url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ",
  "status": "active",
  "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiKmdpZDovL2JjMy9FbWJlZC8xMDMwMDk3NTAyP2V4cGlyZXNfaW4GOwBUSSIIcHVyBjsAVEkiD2F0dGFjaGFibGUGOwBU--10dcfa365b396dfbb686898681ccecb3c96dea3f",
  "type": "video",
  "content_type": "embed/youtube-video",
  "image_url": "https://i.ytimg.com/vi/dQw4w9WgXcQ/hqdefault.jpg",
  "content": ""
}
```
<!-- END GET /embeds/$SGID.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/embeds/$SGID.json
```


Including embeds in rich text
-----------------------------

Check [Inserting an embed](rich_text.md#inserting-an-embed) for details on how to do this.
