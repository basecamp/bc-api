Authentication
==============

> Speak, friend, and enter.

All Basecamp 5 API requests are authenticated by passing along an OAuth 2 token.

- [OAuth 2 overview](#oauth-2-overview)
- [OAuth 2 from scratch](#oauth-2-from-scratch)
- [Get authorization](#get-authorization)
- [Refreshing access tokens](#refreshing-access-tokens)

OAuth 2 overview
----------------

We use [OAuth 2](https://oauth.net/2/) so your users can authorize your application to use Basecamp on their behalf without sharing their credentials.

1. [Grab an OAuth 2 library](https://oauth.net/code/).
2. Register your app at [launchpad.37signals.com/integrations](https://launchpad.37signals.com/integrations). You'll be assigned a `client_id` and `client_secret`. You'll need to provide a `redirect_uri`: a URL where we can send a verification code. Just enter a dummy URL like `http://myapp.com/oauth` if you're not ready for this yet.
3. Configure your OAuth 2 library with your `client_id`, `client_secret`, and `redirect_uri`. Tell it to use `https://launchpad.37signals.com/authorization/new` to request authorization and `https://launchpad.37signals.com/authorization/token` to get access tokens.
4. Try making an authorized request to `https://launchpad.37signals.com/authorization.json` to dig in and test it out! Check out the [Get authorization](#get-authorization) endpoint for a description of what this returns.


OAuth 2 from scratch
--------------------

If you're developing your own OAuth 2 client, here's the full flow.

**TL;DR** request access, receive a verification code, trade it for an access token.

### 1. Redirect the user to Launchpad

```
https://launchpad.37signals.com/authorization/new?response_type=code&client_id=your-client-id&redirect_uri=your-redirect-uri
```

We authenticate their Basecamp ID and ask whether it's ok to give access to your app.

### 2. Receive a verification code

We redirect the user back to your `redirect_uri` with a time-limited verification code.

### 3. Exchange the code for an access token

Your app makes a backchannel POST to trade the verification code for an access token:

```
POST https://launchpad.37signals.com/authorization/token
```

**Required parameters**:

- `grant_type=authorization_code`
- `client_id=your-client-id`
- `redirect_uri=your-redirect-uri`
- `client_secret=your-client-secret`
- `code=verification-code`

The response includes an access token and a refresh token:

```json
{
  "access_token": "BAhbB0kiAbB7ImNsaWVudF9pZCI6IjEyM...",
  "token_type": "Bearer",
  "expires_in": 1209600,
  "refresh_token": "BAhbB0kiAbB7ImNsaWVudF9pZCI6IjEyM..."
}
```

### 4. Use the token to authorize API requests

Set the `Authorization` request header:

```
Authorization: Bearer YOUR_OAUTH_TOKEN
```

Make an authorized request to `https://launchpad.37signals.com/authorization.json` to find the user's identity and available accounts (see [Get authorization](#get-authorization)).

### Legacy parameter support

The legacy parameters `type=web_server` (for authorization and token exchange) and `type=refresh` (for token refresh) are still accepted but not recommended. Use the standard `response_type` and `grant_type` parameters documented above instead.


Get authorization
-----------------

* `GET https://launchpad.37signals.com/authorization.json` will return the authorization details for the authenticated user.

This endpoint requires the `Authorization: Bearer YOUR_OAUTH_TOKEN` header and returns:

- An `expires_at` timestamp for when this token will expire (access tokens have a 2-week lifetime)
- An `identity` with the user's name and email (**not** used for identifying users within Basecamp—use the [Get person][people] endpoints for that)
- A list of `accounts` the user can access, with `href` fields for making API requests

This should be the first request after obtaining a user's authorization token. Pick the account with `"product": "bc3"` and use its `href` as the base URL for Basecamp 5 API requests.

###### Example JSON Response
<!-- START GET https://launchpad.37signals.com/authorization.json -->
```json
{
  "expires_at": "2026-02-16T12:00:00-06:00",
  "identity": {
    "id": 9999999,
    "first_name": "Jason",
    "last_name": "Fried",
    "email_address": "jason@basecamp.com"
  },
  "accounts": [
    {
      "product": "bc3",
      "id": 99999999,
      "name": "Honcho Design",
      "href": "https://3.basecampapi.com/99999999",
      "app_href": "https://3.basecamp.com/99999999"
    }
  ]
}
```
<!-- END GET https://launchpad.37signals.com/authorization.json -->

###### Copy as cURL

```shell
curl -H "Authorization: Bearer $ACCESS_TOKEN" \
  -A 'MyApp (yourname@example.com)' \
  https://launchpad.37signals.com/authorization.json
```

**Note on authenticating users via OAuth**: We don't recommend using the OAuth API to authenticate users in third-party services (e.g. a "Login with Basecamp" button). We don't verify email addresses, so an attacker could gain access using email addresses they don't own.


Refreshing access tokens
-------------------------

Access tokens expire after 2 weeks. Use the refresh token to request a new access token without requiring the user to re-authorize:

```
POST https://launchpad.37signals.com/authorization/token
```

**Required parameters**:

- `grant_type=refresh_token`
- `refresh_token=your-current-refresh-token`
- `client_id=your-client-id`
- `client_secret=your-client-secret`

The response has the same format as the initial token exchange:

###### Example JSON Response
<!-- START POST https://launchpad.37signals.com/authorization/token (refresh) -->
```json
{
  "access_token": "BAhbB0kiAbB7ImNsaWVudF9pZCI6IjEyM...",
  "token_type": "Bearer",
  "expires_in": 1209600,
  "refresh_token": "BAhbB0kiAbB7ImNsaWVudF9pZCI6IjEyM..."
}
```
<!-- END POST https://launchpad.37signals.com/authorization/token (refresh) -->

[people]: people.md#get-person
