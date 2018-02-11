---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

> Web Site

```http
https://twain.hazybits.com
```

> API Endpoint

```http
https://twain-api.hazybits.com
```

Welcome to the TWAIN Cloud API! You can use our API to register, review, and control scanners, 
associated with your TWAIN Cloud account. It is like Google Print, but for scanners :)

You can do all kinds of amazing things with scanners remotely - acquire documents, process 
them in the cloud and retrieve right to your device (PC, Mac, mobile phone - doesn't matter).
API is based on HTTP / websockets, so can be accessed virtually from any platform.

You can view code examples in the dark area to the right, and you can switch the programming language 
of the examples with the tabs in the top right.

Please feel free to follow development process on [GitHub](https://github.com/hazy-bits/twain-cloud) 
and join the discussion! Documentation for the project is hosted on 
[GitHub](https://github.com/hazy-bits/twain-cloud-docs) as well - so in case of any mistakes or 
suggestions please submit an issue there.

## TWAIN Direct vs TWAIN Cloud
[TWAIN Direct](http://www.twaindirect.org/) is an industry standard created by 
[TWAIN Working Grop](http://www.twain.org/). It defines a protocol of communication between 
scanner device and client application. By design, TWAIN Direct does not require scanner drivers, 
i.e. allows 'direct' connection between application and scanner device. Primary goal of the 
standard is to make life of scanner vendors and application writers easier by introducing
cross-platform, technology agnostic language of communication. 

Please check out [TWAIN Direct](http://www.twaindirect.org/) web site for additional details.

## TWAIN Cloud is a standard
TWAIN Cloud is an extension of TWAIN Direct that defines a standard and secure way for scanner 
devices to be used over Internet. This capability enables a number of interesting scenarios, not 
available before:

 - Accessing TWAIN Direct scanners across different networks
 - Remote device management and document aquisition
 - etc.

TWAIN Cloud is an industry standard in its own right which [TWAIN Working Grop](http://www.twain.org/)
owns. Having said that, TWAIN Cloud implementation that [HazyBits](https://hazybits.com) hosts on
[https://twain.hazybits.com](https://twain.hazybits.com) web site is an implementation of the standard,
one of the many possible.

The primary goal of this implementation is to demonstrate what is possible to achieve with modern
image capture tecnologies and how they can change your business processes.


# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct 
# header with each request
curl "api_endpoint_here"
  -H "Authorization: <authorization token>"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
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

# Registration
Registration process

The whole registration process is illustrated on the diagram below:

## Start registration

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

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
---------:|:-------:|:-----------
`include_cats` | `false` | If set to true, the result will also include cats.
`available` | `true` | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
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

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
---------:| -----------
`ID` | The ID of the kitten to retrieve

## Delete a Specific Kitten

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

