# Registration
Registration process

The whole registration process is illustrated on the diagram below:

## Start registration flow

```shell
curl "https://twain-api.hazybits.com/register"
```

```javascript
$.ajax({
    method: 'POST',
    url: apiEndpoint + '/register'
})
```

> The above command returns JSON structured like this:

```json
{
  "sample": "tbd"
}
```

This endpoint begins registration process.

### HTTP Request

`POST https://twain-api.hazybits.com/register`

### Request Payload

Property | Default | Description
---------:|:-------:|:-----------
`include_cats` | `false` | If set to true, the result will also include cats.
`available` | `true` | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Complete registration flow

```shell
curl "https://twain-api.hazybits.com/claim"
  -H "Authorization: <access token>"
```

```javascript
// TODO: add headers and body
$.ajax({
    method: 'POST',
    url: apiEndpoint + '/claim'
})
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint completes registration flow and associates scanner with a user (using information from
`Authorization` header). 

Once registration is complete, 

<aside class="warning">Until registration is complete, scanner can't be used to initiate TWAIN
Cloud jobs.</aside>

### HTTP Request

`GET https://twain-api.hazybits.com/claim`

### Request Payload

Property | Description
---------:| -----------
`ID` | The ID of the kitten to retrieve
