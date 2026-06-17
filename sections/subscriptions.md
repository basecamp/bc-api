Subscriptions
=============

Many of the resources in Basecamp 5 that can be commented on have _subscribers_, that is, people that will get notified when a new comment is added. To know if it's possible to modify the subscriptions for a recording, check its JSON response for the `subscription_url` attribute. This attribute contains the URL to hit to get information about current subscribers and to add/remove subscribers.

Endpoints:

- [Get subscription](#get-subscription)
- [Subscribe current user](#subscribe-current-user)
- [Unsubscribe current user](#unsubscribe-current-user)
- [Update subscription](#update-subscription)


Get subscription
----------------

* `GET /recordings/2/subscription.json` will return subscription information for a recording with an ID of `2`.

###### Example JSON Response
<!-- START GET /recordings/2/subscription.json -->
```json
{
  "subscribed": true,
  "count": 2,
  "url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479406/subscription.json",
  "subscribers": [
    {
      "id": 1049715913,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
      "name": "Victor Cooper",
      "email_address": "victor@honchodesign.com",
      "personable_type": "User",
      "title": "Chief Strategist",
      "bio": "Don’t let your dreams be dreams",
      "location": "Chicago, IL",
      "created_at": "2026-02-12T06:08:49.342Z",
      "updated_at": "2026-02-12T06:08:50.871Z",
      "admin": true,
      "owner": true,
      "client": false,
      "employee": true,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
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
    {
      "id": 1049715938,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--4ccc567a0a3b10e354bca909b704637b601f0b16",
      "name": "Annie Bryan",
      "email_address": "annie@honchodesign.com",
      "personable_type": "User",
      "title": "Central Markets Manager",
      "bio": "To open a store is easy, to keep it open is an art",
      "location": null,
      "created_at": "2026-02-12T06:08:57.340Z",
      "updated_at": "2026-02-12T06:08:57.340Z",
      "admin": false,
      "owner": false,
      "client": false,
      "employee": true,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOJkkT4=--732a71fbd28ec10d9bf4466abd3588a8bea40bdb/avatar",
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
  ]
}
```
<!-- END GET /recordings/2/subscription.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/subscription.json
```

Subscribe current user
----------------------

* `POST /recordings/2/subscription.json` will subscribe the current user to the recording with an ID of `2`. It returns `200 OK` with the current JSON representation of the recording subscriptions if the creation was a success. See the [Get subscription](#get-subscription) endpoint for an example of such response.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/subscription.json
```

Unsubscribe current user
-----------------------

* `DELETE /recordings/2/subscription.json` will unsubscribe the current user from the recording with an ID of `2`. It returns `204 No Content` in any case, even if the current user wasn't previously subscribed.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/subscription.json
```

Update subscription
-------------------

* `PUT /recordings/2/subscription.json` will add and remove the people given from the list of subscribers for the recording with an ID of `2`. It returns `200 OK` with the current JSON representation of the recording subscriptions if the creation was a success.

**Parameters**: Requests should include at least one of the following parameters.

* `subscriptions` - an array of people IDs.
* `unsubscriptions` - an array of people IDs.

###### Example JSON Request
<!-- START PUT PAYLOAD /recordings/2/subscription.json -->
```json
{
  "subscriptions": [
    1049715939
  ],
  "unsubscriptions": [
    1049715913
  ]
}
```
<!-- END PUT PAYLOAD /recordings/2/subscription.json -->


###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"subscriptions":[1049715916], "unsubscriptions":[1049715914]}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/subscription.json
```

###### Example JSON Response
<!-- START PUT /recordings/2/subscription.json -->
```json
{
  "subscribed": false,
  "count": 2,
  "url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069479406/subscription.json",
  "subscribers": [
    {
      "id": 1049715938,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--4ccc567a0a3b10e354bca909b704637b601f0b16",
      "name": "Annie Bryan",
      "email_address": "annie@honchodesign.com",
      "personable_type": "User",
      "title": "Central Markets Manager",
      "bio": "To open a store is easy, to keep it open is an art",
      "location": null,
      "created_at": "2026-02-12T06:08:57.340Z",
      "updated_at": "2026-02-12T06:08:57.340Z",
      "admin": false,
      "owner": false,
      "client": false,
      "employee": true,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOJkkT4=--732a71fbd28ec10d9bf4466abd3588a8bea40bdb/avatar",
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
    {
      "id": 1049715939,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--91bd4d39e2f4af1d814a0b480e809d15a51df239",
      "name": "Cheryl Walters",
      "email_address": "cheryl@honchodesign.com",
      "personable_type": "User",
      "title": "Corporate Integration Director",
      "bio": "A joke is a very serious thing",
      "location": null,
      "created_at": "2026-02-12T06:08:57.659Z",
      "updated_at": "2026-02-12T06:08:57.659Z",
      "admin": false,
      "owner": false,
      "client": false,
      "employee": true,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBONkkT4=--b57b5a44335d4c3ba1a2585abd6e5c7e4c85fdd6/avatar",
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
  ]
}
```
<!-- END PUT /recordings/2/subscription.json -->

Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/recordings/2/subscription.json` → [Get subscription](#get-subscription)
* `POST /buckets/1/recordings/2/subscription.json` → [Subscribe current user](#subscribe-current-user)
* `DELETE /buckets/1/recordings/2/subscription.json` → [Unsubscribe current user](#unsubscribe-current-user)
* `PUT /buckets/1/recordings/2/subscription.json` → [Update subscription](#update-subscription)
