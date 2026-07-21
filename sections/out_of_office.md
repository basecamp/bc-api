Out of office
=============

Endpoints:

- [Get out of office](#get-out-of-office)
- [Enable out of office](#enable-out-of-office)
- [Disable out of office](#disable-out-of-office)


Get out of office
-----------------

* `GET /people/2/out_of_office.json` will return the out of office status for the person with the given ID.

When out of office is not enabled, `enabled` will be `false` and `start_date`,
`end_date`, and `back_on_date` are omitted.

###### Example JSON Response
<!-- START GET /people/2/out_of_office.json -->
```json
{
  "person": {
    "id": 1049715913,
    "name": "Victor Cooper",
    "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
  },
  "enabled": true,
  "ongoing": true,
  "start_date": "2026-07-20",
  "end_date": "2026-07-26",
  "back_on_date": "2026-07-27"
}
```
<!-- END GET /people/2/out_of_office.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/people/2/out_of_office.json
```


Enable out of office
--------------------

* `POST /people/2/out_of_office.json` will enable or replace out of office for the person with the given ID.

Admins on accounts with a Pro Pack can enable out of office on behalf of other people. Otherwise, you can only manage your own out of office.

This endpoint will return `200 OK` with the current JSON representation of the out of office if the creation was a success. If the person already has an out of office set, it will be replaced.

**Required parameters**:

* `start_date` - the start date in ISO 8601 format (e.g. `2026-03-10`).
* `end_date` - the end date in ISO 8601 format (e.g. `2026-03-17`).

###### Example JSON Request

```json
{
  "out_of_office": {
    "start_date": "2026-03-10",
    "end_date": "2026-03-17"
  }
}
```

###### Example JSON Response
<!-- START POST /people/2/out_of_office.json -->
```json
{
  "person": {
    "id": 1049715913,
    "name": "Victor Cooper",
    "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar"
  },
  "enabled": true,
  "ongoing": true,
  "start_date": "2026-07-20",
  "end_date": "2026-07-26",
  "back_on_date": "2026-07-27"
}
```
<!-- END POST /people/2/out_of_office.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"out_of_office": {"start_date": "2026-03-10", "end_date": "2026-03-17"}}' \
  https://3.basecampapi.com/$ACCOUNT_ID/people/2/out_of_office.json
```


Disable out of office
---------------------

* `DELETE /people/2/out_of_office.json` will disable out of office for the person with the given ID.

Admins on accounts with a Pro Pack can disable out of office on behalf of other people. Otherwise, you can only manage your own out of office.

This endpoint will return `204 No Content` if the disable was a success. Disabling when out of office is already off will also return `204 No Content`.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/people/2/out_of_office.json
```
