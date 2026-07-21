Lineup Markers
================

Endpoints:

- [List markers](#list-markers)
- [Create a marker](#create-a-marker)
- [Update a marker](#update-a-marker)
- [Destroy a marker](#destroy-a-marker)

List markers
-----------------------

* `GET /lineup/markers.json` returns all markers for the account.

This endpoint will return `200 OK` with a JSON array of markers.

###### Example JSON Response
<!-- START GET /lineup/markers.json -->
```json
[
  {
    "id": 6750828,
    "created_at": "2026-07-21T00:21:46.309Z",
    "date": "2026-04-06",
    "name": "Spring kickoff",
    "updated_at": "2026-07-21T00:21:46.309Z"
  }
]
```
<!-- END GET /lineup/markers.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  https://3.basecampapi.com/$ACCOUNT_ID/lineup/markers.json
```

Create a marker
-------------------------

* `POST /lineup/markers.json` creates an account-wide marker that shows up in the Lineup.

**Required parameters**:

* `name` of the marker.
* `date` of the marker ISO 8601 formatted without a time part.

This endpoint will return `201 Created` with an empty response body.

###### Example JSON Request

```json
{
  "name": "Anniversary",
  "date": "2021-01-01"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"name": "Anniversary", "date": "2021-01-01"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/lineup/markers.json
```

Update a marker
-----------------------

* `PUT /lineup/markers/1.json` changes name and/or date of the marker with an ID of `1`.

_Optional parameters_:

* `name` of the marker.
* `date` of the marker ISO 8601 formatted without a time part.

This endpoint will return `200 OK` with an empty response body.

###### Example JSON Request

```json
{
  "name": "Updated anniversary"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"name": "Updated anniversary"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/lineup/markers/1.json
```

Destroy a marker
-----------------------

* `DELETE /lineup/markers/1.json` permanently destroys the marker with an ID of `1` immediately.

This endpoint will return `204 No Content`.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/lineup/markers/1.json
```
