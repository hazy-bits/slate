# Registration
Registration process

The whole registration process is illustrated on the diagram below:

![Registration Flow](http://plantuml.com/plantuml/png/fL3D2e904BxlKmmUboJew26GJa5Kk4ddHGTRijbOLv-_yOT8qIuUTx_vVbMcYT11k8VWTe-FPpYKjiu3Y63hi32LHoV6ICYtggT58AMXndY4D3b92Pfo_kg9JdjZ2Rnz8aafH5eDFialVDK51X6GRaoXFMwWhWmL4rqXr49EZlcsPRaSKOWPlqxc4jV-iGE5ha77GfgVIDva78DJjDGrhcFv3fnjtZfntU7ykzR_kJXdnvfVUgdnf49MQlDQK_83)

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
TBD

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
TBD