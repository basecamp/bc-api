Card table wormholes
====================

A wormhole sends cards dropped into it straight to a column on another card table. Wormholes appear in the `wormholes` array of a [card table](card_tables.md#get-a-card-table), titled "Project › Board › Column" after their destination — see that payload for the JSON representation.

Endpoints:

- [Create a wormhole](#create-a-wormhole)
- [Update a wormhole](#update-a-wormhole)
- [Delete a wormhole](#delete-a-wormhole)

Create a wormhole
--------------------------

* `POST /buckets/1/card_tables/2/wormholes.json` creates a wormhole on the card table with ID `2` in the project with ID `1`.

**Required parameters**: `destination_recording_id` — the ID of a column on another card table the requester can access.

This endpoint will return `201 Created` with the current JSON representation of the wormhole if the creation was a success, or `422 Unprocessable Entity` if the card table already holds the maximum of four wormholes.

###### Example JSON Request

```json
{
  "destination_recording_id": 1069480051
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"destination_recording_id":1069480051}' \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/card_tables/2/wormholes.json
```

Update a wormhole
--------------------------

* `PUT /buckets/1/card_tables/wormholes/3.json` changes the destination of the wormhole with ID `3` in the project with ID `1`. The wormhole's title follows its destination.

**Required parameters**: `destination_recording_id` — the ID of a column on another card table the requester can access.

This endpoint will return `200 OK` with the current JSON representation of the wormhole if the update was a success.

###### Example JSON Request

```json
{
  "destination_recording_id": 1069480051
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" -X PUT \
  -d '{"destination_recording_id":1069480051}' \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/card_tables/wormholes/3.json
```

Delete a wormhole
--------------------------

* `DELETE /buckets/1/card_tables/wormholes/3.json` deletes the wormhole with ID `3` in the project with ID `1`.

This endpoint will return `204 No Content` if successful.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/card_tables/wormholes/3.json
```
