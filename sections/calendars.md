Calendars
=========

Available since Basecamp 5: per-account calendars are accessible via
`/calendars/:id.json`, where `:id` is the calendar bucket's id (a Calendar is a
[bucketable][buckets] of its own — distinct from a [project][projects]). The
calendar exposes display metadata (name, color) and a link to its underlying
[schedule][schedules] resource.

Endpoints:

- [Get a calendar](#get-a-calendar)
- [Update a calendar](#update-a-calendar)

[buckets]: ../README.md#recordings-bucket-contents
[projects]: projects.md
[schedules]: schedules.md

Get a calendar
--------------

* `GET /calendars/2.json` returns the [calendar][calendars] with the bucket id `2`.

[calendars]: ../README.md#recordings-bucket-contents

###### Example JSON Response
<!-- START GET /calendars/2.json -->
```json
{
  "id": 2085958497,
  "type": "Calendar",
  "name": "Honcho Design Calendar",
  "color": "blue",
  "created_at": "2026-05-28T17:22:22.133Z",
  "updated_at": "2026-07-20T04:05:52.374Z",
  "url": "https://3.basecampapi.com/195539477/calendars/2085958497.json",
  "app_url": "https://3.basecamp.com/195539477/calendars/2085958497",
  "schedule_url": "https://3.basecampapi.com/195539477/schedules/1069478892.json"
}
```
<!-- END GET /calendars/2.json -->

Update a calendar
-----------------

* `PUT /calendars/2.json` updates the calendar with the bucket id `2`.

###### Permitted parameters

| Param   | Type   | Description |
| ------- | ------ | ----------- |
| `color` | String | One of `white`, `red`, `orange`, `yellow`, `green`, `blue`, `aqua`, `purple`, `gray`, `pink`, `brown`. |

Submitting an unknown color returns `422 Unprocessable Entity` with a JSON
`errors` payload.

###### Example JSON Request
<!-- START PUT PAYLOAD /calendars/2.json -->
```json
{
  "calendar": {
    "color": "blue"
  }
}
```
<!-- END PUT PAYLOAD /calendars/2.json -->

Returns `200 OK` with the updated calendar's JSON shape.
