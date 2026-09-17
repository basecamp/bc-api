People
======

Endpoints:

- [Get all people](#get-all-people)
- [Get people on a project](#get-people-on-a-project)
- [Update who can access a project](#update-who-can-access-a-project)
- [Join a project](#join-a-project)
- [Enroll people](#enroll-people)
- [Add and remove clients on a project](#add-and-remove-clients-on-a-project)
- [Enable or disable clients on a project](#enable-or-disable-clients-on-a-project)
- [Get pingable people](#get-pingable-people)
- [Get person](#get-person)
- [Get my personal info](#get-my-personal-info)
- [Update my personal info](#update-my-personal-info)
- [Get my preferences](#get-my-preferences)
- [Update my preferences](#update-my-preferences)

Get all people
--------------

* `GET /people.json` will return all people visible to the current user.

Wherever a person is represented, the `email_address` is only returned in full to account administrators and owners, and to the person themselves. For everyone else it is redacted (e.g. `"j••••@•••••••••.•••"`).

The `personable_type` field says what kind of person this is — `User`, `Agent`, `Tombstone`, and so on. New types may appear at any time, so handle a value you don't recognize gracefully. See [Person types](../README.md#person-types).

###### Example JSON Response
<!-- START GET /people.json -->
```json
[
  {
    "id": 1049715913,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
    "name": "Victor Cooper",
    "personable_type": "User",
    "title": "Chief Strategist",
    "tagline": "Don't let your dreams be dreams",
    "location": "Chicago, IL",
    "created_at": "2026-05-28T17:22:22.069Z",
    "updated_at": "2026-07-21T00:05:55.167Z",
    "email_address": "victor@honchodesign.com",
    "bio": "Don't let your dreams be dreams",
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
  }
]
```
<!-- END GET /people.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/people.json
```


Get people on a project
------------------------

* `GET /projects/1/people.json` will return all active people on the project with the given ID.

See the [Get all people](#get-all-people) endpoint for an example of the JSON response.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/projects/1/people.json
```

Update who can access a project
--------------------------------

* `PUT /projects/1/people/users.json` allows granting new and existing people access to a project, and revoking access from existing people.

**Parameters**: Requests should include at least one of the following parameters.

* `grant` - an array of people IDs.
* `revoke` - an array of people IDs.
* `create` - an array of new people with `name` and `email_address` properties, and optional `title` and `company_name` properties.

###### Example JSON Request
<!-- START PUT PAYLOAD /projects/1/people/users.json -->
```json
{
  "grant": [
    1049715915
  ],
  "revoke": [
    1049715944
  ],
  "create": [
    {
      "name": "Victor Copper",
      "email_address": "victor@hanchodesign.com",
      "title": "Prankster",
      "company_name": "Hancho Design"
    }
  ]
}
```
<!-- END PUT PAYLOAD /projects/1/people/users.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"grant":[2],"revoke":[3,4]}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/1/people/users.json
```

###### Example JSON Response
<!-- START PUT /projects/1/people/users.json -->
```json
{
  "granted": [
    {
      "id": 1049715915,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--56bb1f99675fd8fe08f93a706a5d2ddaa8412625",
      "name": "Amy Rivera",
      "personable_type": "User",
      "title": "Central Web Coordinator",
      "tagline": "I never said most of the things I said",
      "location": null,
      "created_at": "2026-05-28T17:22:23.206Z",
      "updated_at": "2026-05-28T17:22:23.206Z",
      "email_address": "amy@honchodesign.com",
      "bio": "I never said most of the things I said",
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMtkkT4=--9927c47a4cbee30a7f9aea667882496aba799149/avatar",
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    },
    {
      "id": 1049715956,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk1Nj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e842ca0bf3c9a7c8d03a4dede5fd838e947fe5c1",
      "name": "Victor Copper",
      "personable_type": "User",
      "title": "Prankster",
      "tagline": null,
      "location": null,
      "created_at": "2026-07-21T01:05:54.042Z",
      "updated_at": "2026-07-21T01:05:54.042Z",
      "email_address": "victor@hanchodesign.com",
      "bio": null,
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBPRkkT4=--a31ea55b015ce2f5f714df6e51f42245d949ed3a/avatar",
      "company": {
        "id": 1033447819,
        "name": "Hancho Design"
      },
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    }
  ],
  "revoked": [
    {
      "id": 1049715944,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk0ND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--5c49e7f857f7a2aea319ae399f8b00eb63123ef9",
      "name": "Steve Marsh",
      "personable_type": "User",
      "title": "Legacy Directives Strategist",
      "tagline": "You can do it!",
      "location": null,
      "created_at": "2026-05-28T17:22:31.108Z",
      "updated_at": "2026-05-28T17:22:31.108Z",
      "email_address": "steve@honchodesign.com",
      "bio": "You can do it!",
      "admin": false,
      "owner": false,
      "client": false,
      "employee": true,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBOhkkT4=--b169e35b345bcc26eca6964b7ef7de2c16b6f238/avatar",
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
<!-- END PUT /projects/1/people/users.json -->

Join a project
--------------

* `POST /buckets/1/admissions.json` joins the current person to the project with an ID of `1`, when the project's `admissions` policy lets them in:
  * `team` - any member of the account's team (not clients).
  * `employee` - team members who belong to the account's own company.
  * `invite` - only the account owner. Everyone else has to be added with [Update who can access a project](#update-who-can-access-a-project).

No parameters. No request body.

This is the API equivalent of opening an all-access project in the web app and joining it yourself. It is **not** the same as [Update who can access a project](#update-who-can-access-a-project), which grants or revokes access for other people.

Returns `201 Created` with an empty body if the join succeeded. After a successful join, the project appears in [Get all projects](projects.md#get-all-projects) and [Get a project](projects.md#get-a-project) works for this person.

If the project doesn't exist, or its policy doesn't let the current person in (for example, a client, or anyone other than the owner on an `invite` project), the API returns `404 Not Found`. If the person already has access, nothing changes and the response is a `302 Found` redirect to the project.

`GET /projects.json` only lists projects the current person has already joined, so all-access projects they haven't joined yet don't appear there. Reading a resource inside such a project returns `403 Forbidden` with the URL to join:

```json
{
  "message": "You must first seek admission",
  "admission_url": "https://3.basecampapi.com/195539477/buckets/2085958499/admissions",
  "admission_method": "POST"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/buckets/1/admissions.json
```

Enroll people
-------------

* `POST /account/enrollments/people.json` enrolls one or more people on the account, sending each new person an invitation. Unlike [Update who can access a project](#update-who-can-access-a-project), which grants and revokes access to a single project, this endpoint adds people to the account itself and can optionally grant them access to several projects at once.

The caller must be able to manage people on the account; otherwise the request is rejected with `403 Forbidden`.

**Parameters**:

* `people` - a required array of people to enroll. Each entry must have `name` and `email_address`, and may include an optional `title` and `company_name`. An `email_address` that already belongs to someone on the account re-enrolls that existing person rather than creating a duplicate.
* `project_ids` - an optional array of project IDs to grant the enrolled people access to. IDs that aren't integers, that the caller can't manage people on, or that aren't visible to the caller are silently ignored — the request still succeeds, but access is only granted for the projects that pass those checks, so a `201` does not guarantee every requested project was granted.
* `notify` - an optional boolean (default `true`). When `false` (also accepts `"false"`, `"0"`, `0`), no invitation emails are sent to newly enrolled people.

###### Example JSON Request
<!-- START POST PAYLOAD /account/enrollments/people.json -->
```json
{
  "people": [
    {
      "name": "Victor Copper",
      "email_address": "victor@hanchodesign.com",
      "title": "Prankster",
      "company_name": "Hancho Design"
    },
    {
      "name": "Amy Rivera",
      "email_address": "amy@honchodesign.com"
    }
  ],
  "project_ids": [
    1049715914
  ],
  "notify": true
}
```
<!-- END POST PAYLOAD /account/enrollments/people.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"people":[{"name":"Victor Copper","email_address":"victor@hanchodesign.com"}]}' -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/account/enrollments/people.json
```

The response is a `201 Created` whose body is an array with one entry per enrolled person, in request order. Each entry carries a `status` of `"created"` for a newly invited person or `"existing"` for someone who was already on the account, alongside the full person representation.

###### Example JSON Response
<!-- START POST /account/enrollments/people.json -->
```json
[
  {
    "status": "created",
    "id": 1049715956,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk1Nj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e842ca0bf3c9a7c8d03a4dede5fd838e947fe5c1",
    "name": "Victor Copper",
    "personable_type": "User",
    "title": "Prankster",
    "tagline": null,
    "location": null,
    "created_at": "2026-07-21T01:05:54.042Z",
    "updated_at": "2026-07-21T01:05:54.042Z",
    "email_address": "victor@hanchodesign.com",
    "bio": null,
    "admin": false,
    "owner": false,
    "client": false,
    "employee": false,
    "time_zone": "America/Chicago",
    "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBPRkkT4=--a31ea55b015ce2f5f714df6e51f42245d949ed3a/avatar",
    "company": {
      "id": 1033447819,
      "name": "Hancho Design"
    },
    "can_ping": true,
    "can_manage_projects": false,
    "can_manage_people": false,
    "can_access_timesheet": false,
    "can_access_hill_charts": true
  },
  {
    "status": "existing",
    "id": 1049715915,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--56bb1f99675fd8fe08f93a706a5d2ddaa8412625",
    "name": "Amy Rivera",
    "personable_type": "User",
    "title": "Central Web Coordinator",
    "tagline": "I never said most of the things I said",
    "location": null,
    "created_at": "2026-05-28T17:22:23.206Z",
    "updated_at": "2026-05-28T17:22:23.206Z",
    "email_address": "amy@honchodesign.com",
    "bio": "I never said most of the things I said",
    "admin": false,
    "owner": false,
    "client": false,
    "employee": false,
    "time_zone": "America/Chicago",
    "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMtkkT4=--9927c47a4cbee30a7f9aea667882496aba799149/avatar",
    "can_ping": true,
    "can_manage_projects": true,
    "can_manage_people": true,
    "can_access_timesheet": true,
    "can_access_hill_charts": true
  }
]
```
<!-- END POST /account/enrollments/people.json -->

**Validation and error responses**

Enrollment is all-or-nothing: if any entry can't be enrolled, the whole request is rolled back and nobody is created.

* Per-entry validation failures return `422 Unprocessable Entity` with an `errors` array. Each element names the zero-based `index` of the offending entry and a `messages` list. Messages include `"name is required"`, `"email_address is required"`, `"email_address is invalid"`, and `"email_address is duplicated"` (email addresses must be unique within a single request, compared case-insensitively).

```json
{
  "errors": [
    {
      "index": 1,
      "messages": [
        "email_address is invalid"
      ]
    }
  ]
}
```

* Structural problems with the request return `422 Unprocessable Entity` with a single `error` message. A missing, non-array, or empty `people` value returns `"Provide at least one person with name and email_address."`; an entry that isn't an object returns `"Each entry in people must be an object with name and email_address."`.

```json
{
  "error": "Provide at least one person with name and email_address."
}
```

* When the account has reached its user limit and the request would create at least one new person, the response is `507 Insufficient Storage` with `{ "error": "The user limit for this account has been reached." }`. Re-enrolling only people who already exist on the account succeeds even at the limit.

Add and remove clients on a project
-----------------------------------

* `PUT /projects/1/people/client_users.json` grants and revokes client access to a project, and invites brand-new clients by email.

Clients are external collaborators who log in to see only what you choose to share with them. The project must have client access enabled first — see [Enable or disable clients on a project](#enable-or-disable-clients-on-a-project). This endpoint returns `403 Forbidden` when clients are not enabled on the project.

This is the client-side counterpart to [Update who can access a project](#update-who-can-access-a-project). Only client users may be granted here: a `grant` ID belonging to a team member is rejected rather than cross-graded into client access, and a newly `create`d person is always enrolled as a client. Likewise, `revoke` only removes client users.

**Parameters**: Requests should include at least one of the following parameters.

* `grant` - an array of existing client people IDs to add to the project.
* `revoke` - an array of client people IDs to remove from the project.
* `create` - an array of new clients to invite, each with an `email_address` and optional `name`, `title`, and `company_name` properties. When `name` is omitted it defaults to the email address.

Invitations are all-or-nothing: if any `create` entry is invalid the response is `422 Unprocessable Entity` with an `errors` array naming each bad `email_address` and its `messages`, and if the new addresses would exceed the account's user limit the response is `429 Too Many Requests`. In either case nobody is invited. Addresses that already belong to people on the account don't count toward the limit, and a repeated address counts once.

###### Example JSON Request
```json
{
  "grant": [
    1049715915
  ],
  "revoke": [
    1049715944
  ],
  "create": [
    {
      "name": "Annie Bryan",
      "email_address": "annie@springfield.example.com",
      "title": "Owner",
      "company_name": "Springfield Elementary"
    }
  ]
}
```
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"grant":[2],"revoke":[3,4]}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/1/people/client_users.json
```

The response mirrors [Update who can access a project](#update-who-can-access-a-project): a `granted` and a `revoked` array of the affected [people](#get-person), each with `client` set to `true`.


Enable or disable clients on a project
--------------------------------------

* `POST /projects/1/client_enablement.json` enables client access on a project so clients can be added to it.
* `DELETE /projects/1/client_enablement.json` disables client access on a project.

Enabling clients is a separate, deliberate step from adding them: it turns on the project's client-facing surface and applies the default client visibility. By default the project's timeline and most of its docked tools become visible to clients — the card table, Campfire, and Doors stay private — and content added afterward inherits that default, so you adjust visibility per tool and per item from there. Because enabling reconfigures project-wide client visibility this way, adding clients never enables the project implicitly — enable first, then add.

`POST` returns `403 Forbidden` unless the project can have clients (the account supports clients and the project is a standard project). `DELETE` returns `403 Forbidden` while the project still has any client users; remove them first (see above).

###### Example JSON Response
```json
{
  "clients_enabled": true
}
```
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/projects/1/client_enablement.json
```


Get pingable people
-------------------

* `GET /circles/people.json` will return all people on this Basecamp account who can be pinged.

See the [Get all people](#get-all-people) endpoint for an example of the JSON response.

**Note:** This endpoint is currently not paginated.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/circles/people.json
```


Get person
----------

* `GET /people/2.json` will return the profile for the user with the given ID.

When a person has [out of office][3] enabled, the response will include an `out_of_office` object with `start_date` and `end_date` in ISO 8601 format (`YYYY-MM-DD`).

###### Example JSON Response
<!-- START GET /people/2.json -->
```json
{
  "id": 1049715928,
  "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkyOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--35b1370e6239e9a565c0e8f66bed307c7cc488b6",
  "name": "Mark Campbell",
  "personable_type": "User",
  "title": "Principal Markets Supervisor",
  "tagline": null,
  "location": null,
  "created_at": "2026-05-28T17:22:27.508Z",
  "updated_at": "2026-05-28T17:22:27.508Z",
  "email_address": "mark@honchodesign.com",
  "bio": null,
  "admin": false,
  "owner": false,
  "client": false,
  "employee": false,
  "time_zone": "America/Chicago",
  "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNhkkT4=--cef810620a2f44a2144ab788d90679e478ea2344/avatar",
  "can_ping": true,
  "can_manage_projects": true,
  "can_manage_people": true,
  "can_access_timesheet": true,
  "can_access_hill_charts": true
}
```
<!-- END GET /people/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/people/2.json
```


Get my personal info
--------------------

* `GET /my/profile.json` will return the current user's personal info.

See the [Get person](#get-person) endpoint for an example of the JSON response.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/profile.json
```


Update my personal info
-----------------------

* `PUT /my/profile.json` allows updating the current user's personal info.

**Optional parameters**:

* `name` - the user's display name.
* `email_address` - the user's email address. This is the 37signals login identity shared across
  every account, so changing it requires a trusted client with session-equivalent authority: a
  full-scope, identity-wide token (a personal access token, or a first-party app's identity-wide
  token). Any other token gets `403 Forbidden` with an `error` message and changes nothing.
* `title` - the user's job title.
* `bio` - a short bio.
* `location` - the user's location.
* `time_zone_name` - the user's time zone (e.g. `America/Chicago`).
* `first_week_day` - the first day of the week (`0` for Sunday, `1` for Monday).
* `time_format` - time display format.

This endpoint will return `204 No Content` if the update was a success. Returns `422 Unprocessable Entity` if the update fails (e.g. the email address is already in use).

###### Example JSON Request

```json
{
  "name": "Victor Cooper",
  "title": "Chief Strategist",
  "bio": "Don't let your dreams be dreams",
  "location": "Chicago, IL"
}
```
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"name":"Victor Cooper","title":"Chief Strategist"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/my/profile.json
```


Get my preferences
------------------

* `GET /my/preferences.json` will return the current user's preferences.

`time_zone_name` is returned as a Rails-style name (`Central Time (US &
Canada)`). Updates also accept IANA identifiers (`America/Chicago`), which
are normalized to the matching Rails-style name before saving.

###### Example JSON Response
<!-- START GET /my/preferences.json -->
```json
{
  "url": "https://3.basecampapi.com/195539477/my/preferences.json",
  "app_url": "https://3.basecamp.com/195539477/my/preferences",
  "time_zone_name": "Central Time (US & Canada)",
  "first_week_day": "Sunday",
  "time_format": "twelve_hour"
}
```
<!-- END GET /my/preferences.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/my/preferences.json
```


Update my preferences
---------------------

* `PUT /my/preferences.json` will update the current user's preferences.

All parameters are optional. Only include the ones you want to change. These parameters should be sent inside the top-level `person` object in the JSON request body.

* `time_zone_name` - the user's time zone (e.g. `America/Chicago`, `London`, `UTC`). Accepts any valid Rails time zone name.
* `first_week_day` - the first day of the week. Accepts: `Sunday`, `Monday`, `Tuesday`, `Wednesday`, `Thursday`, `Friday`, `Saturday`.
* `time_format` - the time display format. Accepts: `twelve_hour`, `twenty_four_hour`.

Returns `200 OK` with the updated [preferences](#get-my-preferences) JSON representation.

###### Example JSON Request
<!-- START PUT PAYLOAD /my/preferences.json -->
```json
{
  "person": {
    "time_zone_name": "London",
    "first_week_day": "Monday",
    "time_format": "twenty_four_hour"
  }
}
```
<!-- END PUT PAYLOAD /my/preferences.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"person":{"time_zone_name":"London","first_week_day":"Monday","time_format":"twenty_four_hour"}}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/my/preferences.json
```

[3]: out_of_office.md#out-of-office