# Scanner Management

## Get list of registered scanners

```shell
curl "https://twain-api.hazybits.com/scanners"
```

```javascript
$.ajax({
    method: 'GET',
    url: apiEndpoint + '/scanners',
});
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": "fb7e3325-4d3a-4c9c-a6b4-9b83d2551951",
    "manufacturer": "TWAIN",
    // TBD
  },

  // ...
  // the rest of scanners, registered with the cloud.
]
```

> In case of any error, response is as follows:

```json
TBD
```

User may retrieve all scanners registered in TWAIN Cloud.

### HTTP Request

`GET https://twain-api.hazybits.com/scanners`

### Query Parameters

Parameter | Description
--------- | -----------

### Response Payload

Success response payload:

Parameter | Description
--------- | -----------

Error response payload:

Parameter | Description
--------- | -----------

## Get scanner information

```shell
curl "https://twain-api.hazybits.com/scanners/{scannerId}"
```

```javascript
$.ajax({
    method: 'GET',
    url: apiEndpoint + '/scanners/{scannerId}',
});
```

> The above command returns JSON structured like this:

```json
TBD
```

> In case of any error, response is as follows:

```json
TBD
```

User may delete registered scanner from the cloud using this endpoint.

### HTTP Request

`GET https://twain-api.hazybits.com/scanners/{scannerId}`

### Query Parameters

Parameter | Description
--------- | -----------
`scannerId` | Unique ID of the scanner to get information about.

### Response Payload

Success response payload:

Parameter | Description
--------- | -----------

Error response payload:

Parameter | Description
--------- | -----------

## Delete scanner

```shell
curl -X "DELETE" "https://twain-api.hazybits.com/scanners/{scannerId}"
```

```javascript
$.ajax({
    method: 'DELETE',
    url: apiEndpoint + '/scanners/{scannerId}',
});
```

> The above command returns JSON structured like this:

```json
TBD
```

> In case of any error, response is as follows:

```json
TBD
```

User may delete registered scanner from the cloud using this endpoint.

### HTTP Request

`DELETE https://twain-api.hazybits.com/scanners/{scannerId}`

### Query Parameters

Parameter | Description
--------- | -----------
`scannerId` | Unique ID of the scanner to delete from the cloud.

### Response Payload

Success response payload:

Parameter | Description
--------- | -----------

Error response payload:

Parameter | Description
--------- | -----------