Chatbots
========

There are two types of chatbots in Basecamp: Those that are interactive and those that only post content on their own.
Interactive chatbots can be queried or commanded by anyone in any room. You can even start a ping conversation with one.

Both types of chatbots are authenticated differently from how the rest of the API works. There's no OAuth exchange to perform.
Interactive chatbots have their queries and commands POST'ed directly to them with a piece of JSON. Whatever they return to
that POST is inserted into the room where the conversation is happening.

Alternatively, if a chatbot needs to post on their own, there's a special key'ed URL that's all that is needed. It's returned
as `lines_url` when creating a chatbot. See the [Create a chatbot](#create-a-chatbot) endpoint for more info. If you have that
URL, you can post content as that chatbot to that room. But what you can't do is read anything from the room. This is not a
streaming service. It's intended purely for request/reply and blind reply interactions.

When an interactive chatbot is invoked, it'll receive a JSON payload like this:

```json
{
  "command": "What up?",
  "creator": {
    "id": 1007299143,
    "attachable_sgid": "BAh7CEkiCGdpZAY6BkVUSSIrZ2lkOi8vYmMzL1BlcnNvbQQcMDA3Mjk5MTQzP2V4cGlyZXNfaW4GOwBUSSIMcHVycG9zZQY7AFRJIg9hdHRhY2hhYmxlBjsAVEkiD2V4cGlyZXNfYXQGOwBUMA==--919d2c8b11ff403eefcab9db42dd26846d0c3102",
    "name": "Victor Cooper",
    "email_address": "victor@honchodesign.com",
    "personable_type": "User",
    "title": "Chief Strategist",
    "bio": "Don't let your dreams be dreams",
    "created_at": "2016-09-22T16:21:03.625-05:00",
    "updated_at": "2016-09-22T16:21:06.184-05:00",
    "admin": true,
    "owner": true,
    "time_zone": "America/Chicago",
    "avatar_url": "https://3.basecamp-static.com/195539477/people/BAhpBEcqCjw=--c632b967cec296b87363a697a67a87f9cc1e5b45/avatar-64-x4",
    "company": {
      "id": 1033447817,
      "name": "Honcho Design"
    }
  },
  "callback_url": "https://3.basecamp.com/195539477/integrations/2uH9aHLEVhhaXKPaqrj8yw8P/buckets/2085958501/chats/9007199254741775/lines"
}
```

You can use the information in the creator block to enforce permission controls. If you have a deploy bot, then maybe only certain
people, with pre-specified IDs, will be able to interact with it.

If the interactive chatbot is able to provide a response right away, it can, as stated above, just return that as part
of a text/html content-typed response with status code 200. This response has the same format as all other rich text in Basecamp,
but also accepts these additional tags: `table tr td th thead tbody details summary`. The pair of details/summary is particularly
useful for providing large chunks of information hidden behind a show/hide.

Here are a few examples of return content or content sent to the callback URL from what we use at Basecamp:

Alert warning from Nagios with inline resolution links:

```html
<details><summary><a href="https://example.com">🔴 CRITICAL some.ip.37signals.com Http Profile /Common/bc3_anycast_production_https_profile</a></summary><pre>CRIT - High Error Levels - 20 4xx, 0 5xx</pre>
<p><strong>Unacknowledged</strong></p>
<p>
  <a href="https://example.com/ack">Acknowledge</a> |
  <a href="https://example.com/disnotif">Disable Notifications</a> |
  <a href="https://example.com/down">Schedule 2hr Downtime</a>
</p>
<p>Status changed less than a minute ago and was previously Warning.</p>
</details>
```

Status update from AWS:

```html
<table border="1">
<tbody>
  <tr>
      <th>Service</th>
      <th>Message</th>
      <th>Date/Time</th>
   </tr>
   <tr>
      <td>DIRECTCONNECT</td>
      <td><a href="http://status.aws.amazon.com/#directconnect-us-east-1_1474053063">Informational message: Network Connectivity</a></td>
      <td>Fri, 16 Sep 2016 12:11:03 -0700</td>
   </tr>
   <tr>
      <td>INTERNETCONNECTIVITY</td>
      <td><a href="http://status.aws.amazon.com/#internetconnectivity-eu-west-1_1474374660">Service is operating normally: [RESOLVED] Network Connectivity</a></td>
      <td>Tue, 20 Sep 2016 05:31:00 -0700</td>
   </tr>
   <tr>
      <td>INTERNETCONNECTIVITY</td>
      <td><a href="http://status.aws.amazon.com/#internetconnectivity-us-west-1_1474645633">Informational message: Network Connectivity</a></td>
      <td>Fri, 23 Sep 2016 08:47:13 -0700</td>
   </tr>
   <tr>
      <td>INTERNETCONNECTIVITY</td>
      <td><a href="http://status.aws.amazon.com/#internetconnectivity-us-west-2_1473841860">Service is operating normally: [RESOLVED] Network Connectivity</a></td>
      <td>Wed, 14 Sep 2016 01:31:00 -0700</td>
   </tr>
   <tr>
      <td>SQS</td>
      <td><a href="http://status.aws.amazon.com/#sqs-ap-southeast-2_1474400640">Service is operating normally: [RESOLVED] Increased API Error Rates</a></td>
      <td>Tue, 20 Sep 2016 12:44:00 -0700</td>
   </tr>
</tbody>
</table>
```

It's important to note that chatbots are account-wide, but with basecamp-specific callback URLs. So you create a chatbot on a specific
Basecamp to get the callback URL for that Basecamp, but the chatbot will instantly be available to every other Basecamp on the account as well.
This also means that any edits or deletes of chatbots are account-wide. For this reason, chatbots can only be managed by administrators.
But everyone is able to interact with interactive chatbots and all you need to post as a chatbot is that callback URL.

Endpoints:

- [Get chatbots](#get-chatbots)
- [Get a chatbot](#get-a-chatbot)
- [Create a chatbot](#create-a-chatbot)
- [Update a chatbot](#update-a-chatbot)
- [Destroy a chatbot](#destroy-a-chatbot)
- [Create a line](#create-a-line)

Get chatbots
------------

* `GET /buckets/1/chats/1/integrations.json` will return all the chatbots from the account with the line URL for the campfire.

###### Example JSON Response
<!-- START GET /buckets/1/chats/1/integrations.json -->
```json
[
  {
    "id": 1049715953,
    "created_at": "2026-05-28T17:29:05.374Z",
    "updated_at": "2026-05-28T17:29:05.374Z",
    "service_name": "Capistrano",
    "command_url": null,
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958/integrations/1049715953.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958/integrations/1049715953",
    "lines_url": "https://3.basecampapi.com/195539477/integrations/oneBqw5TTvLWcJJWLmuHPNC9/buckets/2085958502/chats/1069478958/lines"
  }
]
```
<!-- END GET /buckets/1/chats/1/integrations.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/chats/1/integrations.json
```

Get a chatbot
-------------

* `GET /buckets/1/chats/1/integrations/3.json` will return the chatbot with an ID of `3`, including its line URL.

###### Example JSON Response
<!-- START GET /buckets/1/chats/1/integrations/3.json -->
```json
{
  "id": 1049715953,
  "created_at": "2026-05-28T17:29:05.374Z",
  "updated_at": "2026-05-28T17:29:05.374Z",
  "service_name": "Capistrano",
  "command_url": null,
  "url": "https://3.basecampapi.com/195539477/buckets/2085958502/chats/1069478958/integrations/1049715953.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/chats/1069478958/integrations/1049715953",
  "lines_url": "https://3.basecampapi.com/195539477/integrations/oneBqw5TTvLWcJJWLmuHPNC9/buckets/2085958502/chats/1069478958/lines"
}
```
<!-- END GET /buckets/1/chats/1/integrations/3.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/chats/1/integrations/3.json
```

Create a chatbot
----------------

* `POST /buckets/1/chats/1/integrations.json` creates a chatbot on the account and returns the new chatbot with its lines URL.

**Required parameters**: `service_name` for the chatbot name, which will be used to invoke queries and commands on interactive bots.
No spaces, emoji or non-word characters are allowed, as you need to be able to call it like `!tally myCommand`
_Optional parameters_: `command_url` for the HTTPS url that Basecamp should call when the bot is addressed.

This endpoint will return `201 Created` with the current JSON representation of the chatbot if the creation was a success. See the [Get a chatbot](#get-a-chatbot) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "service_name": "tally",
  "command_url": "https://example.com/endpoint"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"service_name":"tally","command_url":"https://example.com/endpoint"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/chats/1/integrations.json
```

Update a chatbot
----------------

* `PUT /buckets/1/chats/1/integrations/3.json` allows changing the service name and commandURL of the chatbot with an ID of `3`.

**Required parameters**: `service_name` for the chatbot name, which will be used to invoke queries and commands on interactive bots.
No spaces, emoji or non-word characters are allowed, as you need to be able to call it like `!tally myCommand`
_Optional parameters_: `command_url` for the HTTPS url that Basecamp should call when the bot is addressed.

This endpoint will return `200 OK` with the current JSON representation of the chatbot if the update was a success. See the [Get a chatbot](#get-a-chatbot) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "service_name": "uptime",
  "command_url": "https://example.com/endpoint"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"service_name":"uptime","command_url":"https://example.com/endpoint"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/chats/1/integrations/3.json
```

Destroy a chatbot
-----------------

* `DELETE /buckets/1/chats/1/integrations/3.json` will delete the chatbot with an ID of `3` across the account.

This endpoint will return `204 No Content` if the destroy was a success.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/chats/1/integrations/3.json
```

Create a line
-------------

**Note:** This endpoint uses the full project-scoped URL because it authenticates via the chatbot's access key, not via OAuth. The `/buckets/{project_id}/` prefix is required.

* `POST /integrations/$CHATBOT_KEY/buckets/1/chats/2/lines.json` creates a line in the Campfire with ID `2` in the project with ID `1`.

**Required parameters**: `content` as the body for the Campfire line. See our [Rich text guide][1] for what HTML tags are allowed.

_Optional parameters_:

* `content_param` - modifies the name of the required `content` param to support webhooks from a third-party, e.g. Slack with a `text` param

In addition to the tags permitted for all rich text, the following tags are permitted for chatbot lines: `table`, `tr`, `td`, `th`, `thead`, `tbody`, `details`, and `summary`.

This endpoint will return `201 Created` if the creation was a success.

###### Example JSON Request

```json
{
  "content": "Good morning"
}
```

###### Copy as cURL

```shell
curl -s -H "Content-Type: application/json" -d '{"content":"Good morning"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/integrations/$CHATBOT_KEY/buckets/1/chats/2/lines.json
```

or, with a custom content_param called `text`:

```shell
curl -s -H "Content-Type: application/json" -d '{"text":"Good morning"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/integrations/$CHATBOT_KEY/buckets/1/chats/2/lines.json?content_param=text
```


[1]: rich_text.md
