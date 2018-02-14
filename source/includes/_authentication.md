# Authentication

> To authorize, use this code:

```shell
curl "api_endpoint_here"
  -H "Authorization: <authorization token>"
```

> Make sure to replace **authorization token** placeholder with correct token.

<aside class="notice">
<b>TWAIN Cloud Standard</b> does not define authentication mechanism (different implementations
may have conflicting authentication requirements). Instead, TWAIN Cloud explicitly defines which 
methods <b>should</b> be authorized to ensure overall security of the solution. Implementations are 
strongly advised to follow these recommendations.
</aside>

HazyBits TWAIN Cloud implementation relies on OAuth2 authorization framework to exchange
user's Facebook access token to a pair of TWAIN Cloud tokens:

 - Access Token 
 - Refresh Token

**Access token** should be passed with every request in `Authorization` HTTP header. Access token
has an expiration time (1 hour by default) after which it should be refreshed using **refresh token**.

Diagram below illustrate the whole authentication process:

## Login endpoint
TBD

## Logout endpoint
TBD

## Refresh token endpoint
TBD
