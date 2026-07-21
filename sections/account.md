Account
=======

Endpoints:

- [Get account](#get-account)
- [Update account name](#update-account-name)
- [Update account logo](#update-account-logo)
- [Remove account logo](#remove-account-logo)

Get account
-----------

* `GET /account.json` will return the account for the current access token.

The `logo` field is only present when the account has a logo configured. It is omitted entirely when no logo exists.

###### Example JSON Response
<!-- START GET /account.json -->
```json
{
  "id": 1009501286,
  "name": "Honcho Design",
  "owner_name": "Victor Cooper",
  "active": true,
  "created_at": "2026-05-28T17:22:22.057Z",
  "updated_at": "2026-07-20T20:06:02.489-05:00",
  "trial": false,
  "trial_ends_on": null,
  "frozen": false,
  "paused": false,
  "limits": {
    "can_create_projects": true,
    "can_pin_projects": true,
    "can_create_users": true,
    "can_upload_files": true
  },
  "subscription": {
    "short_name": "ClientsV1",
    "proper_name": "Basecamp With Clients",
    "project_limit": null,
    "teams": true,
    "clients": true,
    "templates": true,
    "logo": true,
    "timesheet": true
  },
  "settings": {
    "company_hq_enabled": false,
    "teams_enabled": true,
    "projects_enabled": true
  }
}
```
<!-- END GET /account.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/account.json
```

Update account name
-------------------

* `PUT /account/name.json` will rename the current account. Only account owners can use this endpoint — returns `403 Forbidden` for non-owners.

**Required parameters**:

* `name` - the new name for the account. Returns `400 Bad Request` when blank.

This endpoint returns `200 OK` with the full [account](#get-account) JSON representation on success.

###### Example JSON Request

```json
{
  "name": "Honcho Design Studio"
}
```

###### Example JSON Response
<!-- START PUT /account/name.json -->
```json
{
  "id": 1009501286,
  "name": "Honcho Design Studio",
  "owner_name": "Victor Cooper",
  "active": true,
  "created_at": "2026-05-28T17:22:22.057Z",
  "updated_at": "2026-07-21T01:06:02.969Z",
  "trial": false,
  "trial_ends_on": null,
  "frozen": false,
  "paused": false,
  "limits": {
    "can_create_projects": true,
    "can_pin_projects": true,
    "can_create_users": true,
    "can_upload_files": true
  },
  "subscription": {
    "short_name": "ClientsV1",
    "proper_name": "Basecamp With Clients",
    "project_limit": null,
    "teams": true,
    "clients": true,
    "templates": true,
    "logo": true,
    "timesheet": true
  },
  "settings": {
    "company_hq_enabled": false,
    "teams_enabled": true,
    "projects_enabled": true
  }
}
```
<!-- END PUT /account/name.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -X PUT \
  -d '{"name":"Honcho Design Studio"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/account/name.json
```

Update account logo
-------------------

* `PUT /account/logo.json` will upload or replace the account logo. Only administrators and account owners can use this endpoint — returns `403 Forbidden` for others.

Account logos use direct multipart file upload rather than the standard two-stage `/attachments` flow used elsewhere in the API.

**Required parameters**:

* `logo` - the logo image file, sent as a multipart form upload. Accepted formats: PNG, JPEG, GIF, WebP, AVIF, HEIC. Maximum file size: 5 MB. Returns `422 Unprocessable Entity` when the file is missing, the format is invalid, or the file exceeds 5 MB.

Returns `204 No Content` on success.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -X PUT \
  -F "logo=@company-logo.png" \
  https://3.basecampapi.com/$ACCOUNT_ID/account/logo.json
```

Remove account logo
-------------------

* `DELETE /account/logo.json` will remove the account logo. Only administrators and account owners can use this endpoint — returns `403 Forbidden` for others.

Returns `204 No Content` on success.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/account/logo.json
```
