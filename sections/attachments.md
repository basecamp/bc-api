Attachments
===========

Endpoints:

- [Create an attachment](#create-an-attachment)


Create an attachment
--------------------

* `POST /attachments.json` uploads a file.

**Required request data**: The request body should be the file's raw binary data.

**Required request headers**: `Content-Type` and `Content-Length` for the file.

**Required URI query parameters**: `name` as the file name.

This endpoint will return `201 Created` with the attachment's `attachable_sgid` in the JSON representation.

###### Example JSON Response
<!-- START POST /attachments.json -->
```json
{
  "id": 1046628513,
  "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg1MTM_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--f4fec6f98ff48e45ceb144416a3a68234452a864",
  "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg1MTM_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--f4fec6f98ff48e45ceb144416a3a68234452a864",
  "status_url": "https://upload.3.basecamp.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg1MTM_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--f4fec6f98ff48e45ceb144416a3a68234452a864.json",
  "caption": null,
  "byte_size": 1281,
  "content_type": "image/png",
  "width": 164,
  "height": 39,
  "key": "f628dbcc65dd018a72ae025824ffa8fb4fe3ecf8",
  "filename": "company-logo.png",
  "download_url": "https://storage.3.basecamp.com/195539477/blobs/f628dbcc65dd018a72ae025824ffa8fb4fe3ecf8/download/company-logo.png",
  "previewable": true,
  "preview_url": "https://preview.3.basecamp.com/195539477/blobs/f628dbcc65dd018a72ae025824ffa8fb4fe3ecf8/previews/full",
  "thumbnail_url": "https://preview.3.basecamp.com/195539477/blobs/f628dbcc65dd018a72ae025824ffa8fb4fe3ecf8/previews/card"
}
```
<!-- END POST /attachments.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  --data-binary @pizza.png \
  -H "Content-Type: image/png" -H "Content-Length: 123" \
  https://3.basecampapi.com/$ACCOUNT_ID/attachments.json?name=pizza.png
```

Including attachments in rich text in other recordings
------------------------------------------------------

Check [Inserting an image or file attachment](rich_text.md#inserting-an-image-or-file-attachment) for details on how to do this.
