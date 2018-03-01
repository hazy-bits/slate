# Device Registration

## Overview

Scanner device should be registered with TWAIN Cloud and associated
with a user account before it can be used. From scanner device standpoint
the flow looks as follows:

![Registration Flow](images/registration_flow.png)

The whole process is more complex since it requires user interaction.
Complete registration sequence is illustrated on the diagram below:

![Registration Sequence](images/registration_sequence.png)

## Start registration flow

```shell
curl "https://twain-api.hazybits.com/register"
```

```javascript
$.ajax({
    method: 'POST',
    url: apiEndpoint + '/register',
    contentType: 'application/json',
    data: JSON.stringify({
      // TBD
    })
});
```

> The above command returns JSON structured like this:

```json
{
  "registrationToken": "<registration token>",
  "pollingUrl": "<polling URL>",
  "inviteUrl": "<invite URL>"
}
```

This endpoint begins registration process.

### HTTP Request

`POST https://twain-api.hazybits.com/register`

### Request Payload

TBD (scanner attributes)

### Response Payload

Parameter | Description
--------- | -----------
`registrationToken` | Secret token that should be provided by user to claim the scanner.
`pollingUrl` | URL to be used by scanner device to poll registration status.
`inviteUrl` | URL to be used by user to claim the scanner.

## Poll Registration Status

```shell
curl "https://twain-api.hazybits.com/poll?scannerId={scannerId}"
```

```javascript
$.ajax({
    method: 'GET',
    url: apiEndpoint + '/poll?scannerId={scannerId}',
});
```

> The above command returns JSON structured like this:

```json
{ 
  "success": true, 
  "accessToken": "{accessToken}",
  "refreshToken": "{refreshToken}"
}
```

> In case of any error, response is as follows:

```json
{
  "success": false,
  "message": "Error message",
}
```

Scanner device use this endpoint to poll TWAIN Cloud server and check
if registration process is complete (user claimed the device successfully).

It is recommended to poll the server with some delay before retries.
5 seconds delay is reasonable default.

### HTTP Request

`GET https://twain-api.hazybits.com/poll?scannerId={scannerId}`

### Query Parameters

Parameter | Description
--------- | -----------
`scannerId` | Unique ID of the scanner to check registration status for.

### Response Payload

Success response payload:

Parameter | Description
--------- | -----------
`success` | `True` in case of success registration.
`accessToken` | Access token to be used by scanner to authorize calls to TWAIN Cloud endpoints.
`refreshToken` | Refresh token to be used to get a new pair of access/refresh tokens.

Error response payload:

Parameter | Description
--------- | -----------
`success` | `False` in case incomplete registration.
`message` | Technical message related to the request. 

## Claim Device

```shell
curl "https://twain-api.hazybits.com/claim"
  -H "Authorization: <access token>"
```

```javascript
// TODO: add headers and body
$.ajax({
    method: 'POST',
    url: apiEndpoint + '/claim',
    contentType: 'application/json',
    data: JSON.stringify({ 
      scannerId: '{scannerId}',
      registrationToken: '{registrationToken}'
    })
});
```

> The above command returns JSON structured like this:

```json
{
  // TBD
}
```

This endpoint completes registration flow and associates scanner with a user (using information from
`Authorization` header). 

Once registration is complete, 

<aside class="warning">Until registration is complete, scanner can't be used to initiate TWAIN
Cloud jobs.</aside>

### HTTP Request

`POST https://twain-api.hazybits.com/claim`

### Request Payload

Parameter | Description
--------- | -----------
`scannerId` | Unique ID of the scanner to be claimed.
`registrationToken` | Registration token that was provided during scanner registration.

### Response Payload

TBD (scanner attributes)