Hill charts
===========

Hill charts visualize the progress of to-do lists on a hill-shaped curve, from "figuring things out" (uphill) to "making it happen" (downhill). Each tracked to-do list appears as a dot on the hill.

Hill charts belong to a [to-do set][2]. To get the to-do set ID for a project, see the [Get a project][1] endpoint's `dock` payload.

Endpoints:

- [Get hill chart](#get-hill-chart)
- [Update hill chart settings](#update-hill-chart-settings)


Get hill chart
--------------

* `GET /todosets/1/hill.json` will return the hill chart for the to-do set with an ID of `1`.

###### Example JSON Response
<!-- START GET /todosets/1/hill.json -->
```json
{
  "enabled": true,
  "stale": false,
  "updated_at": "2026-07-21T00:01:19.857Z",
  "app_update_url": "https://3.basecamp.com/195539477/buckets/2085958505/todosets/1069479829/hill/edit",
  "dots": [
    {
      "id": 1069479863,
      "label": "Background and research",
      "color": "blue",
      "position": 0,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todolists/1069479863.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todolists/1069479863"
    }
  ]
}
```
<!-- END GET /todosets/1/hill.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/todosets/1/hill.json
```


Update hill chart settings
--------------------------

* `PUT /todosets/1/hills/settings.json` allows tracking and untracking to-do lists on the hill chart for the to-do set with an ID of `1`.

Pass to-do list IDs to `tracked` and/or `untracked` arrays. Both are optional; you can track, untrack, or do both in a single request. Tracking the first to-do list enables the hill chart. Untracking the last to-do list disables it.

_Optional parameters_:

* `tracked` - an array of to-do list IDs to start tracking on the hill chart.
* `untracked` - an array of to-do list IDs to stop tracking on the hill chart.

Returns `200 OK` with the updated [hill chart](#get-hill-chart) JSON representation.

###### Example JSON Request

```json
{
  "tracked": [1069479573],
  "untracked": [1069479511]
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"tracked": [1069479573]}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/todosets/1/hills/settings.json
```


[1]: projects.md#get-a-project
[2]: todosets.md#get-to-do-set
