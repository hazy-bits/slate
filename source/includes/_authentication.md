# Authentication

> To authorize a request, pass **access token** in **Authorization** header::

```shell
curl "api_endpoint_here"
  -H "Authorization: {accessToken}"
```

> Make sure to replace **accessToken** placeholder with the correct token.

<aside class="notice">
<b>TWAIN Cloud Standard</b> does not define authentication specifics, like the structure of
authentication token, time of expiry, etc. Different implementations may have conflicting
authentication and authorization requirements. Instead, TWAIN Cloud explicitly defines which
methods <b>should</b> be authorized to ensure overall security of the solution. Implementations
are strongly advised to follow these recommendations.
</aside>

HazyBits TWAIN Cloud implementation relies on OAuth2 authorization framework to exchange
user's Facebook access token to a pair of TWAIN Cloud tokens:

- Access Token
- Refresh Token

**Access token** should be passed along with every request in `Authorization` HTTP header. Access token
has an expiration time (1 hour by default) after which it should be refreshed using **refresh token**.

**Refresh token** can be used only once to get a new pair of access/refresh tokens.

## Login endpoint

> Start login flow using the following request:

```shell
curl "https://twain-api.hazybits.com/signin"
```

```javascript
$.ajax({
    method: 'GET',
    url: apiEndpoint + '/signin'
})
```

This endpoint begins OAuth2 login flow. There is a series of GET requests,
connected through HTTP redirects:

- It starts with a redirect to Facebook login form for TWAIN Cloud application 
that asks user to authorize the access to Facebook profile. The following permissions are used:
 - [public_profile](https://developers.facebook.com/docs/facebook-login/permissions/#reference-public_profile)
 - [email](https://developers.facebook.com/docs/facebook-login/permissions/#reference-email)

- Once user authorized access to Facebook profile, another redirect is 
issued to TWAIN Cloud callback URL.

- Finally, TWAIN Cloud generates a pair of access and refresh tokens 
and redirects back to the origin URL passing the tokens in query string.

Diagram below illustrates the whole authentication process:

![Login Flow](images/login_sequence.png)

### HTTP Request

`GET https://twain-api.hazybits.com/signin`

### Query Parameters

Parameter | Description
--------- | -----------
origin | Origin
query  | URL-encoded query string to add to the redirect URL.

## Refresh token endpoint

> Refresh access token using the following request:

```shell
curl "https://twain-api.hazybits.com/refresh/{refreshToken}"
```

```javascript
$.ajax({
    method: 'POST',
    url: apiEndpoint + `/refresh/${refreshToken}`
})
```

> Make sure to replace **refreshToken** placeholder with the correct token.

> The above command returns JSON structured like this:

```json
{
  "accessToken": "{renewed access token}", 
  "refreshToken": "{new refresh token}"
}
```

Since access tokens have a short lifetime (1 hour by default), they need to
be refreshed by an application. To request access token refresh, application
needs to exchange refresh token to a new pair of access / refresh tokens.

<aside class="notice">
Refresh token can be exchanged only one. After that it expires.
</aside>

### HTTP Request

`GET https://twain-api.hazybits.com/refresh/{refreshToken}`

### URL Parameters

Parameter | Description
--------- | -----------
`refreshToken` | Previously issued refresh token for exchange.
