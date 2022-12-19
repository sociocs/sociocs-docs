---
title: Get contact
order: -300
---

Get a contact.

## Method

[!badge GET]

## Path

`/contact/[phone_number]`

## Path parameter

Name | Value | Required? {class="compact"}
--- | ---
phone_number | {{include "api/phone-number-value"}} | Yes

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Description {class="compact"}
--- | ---
status | `success` or `error` | -
errors | Array of object `{ msg: [error detail] }` | Only present when status is `error`
data | Object of contact fields | Only present when status is `success`

## Code sample

+++ cURL

```shell
curl --location --request GET 'https://api.sociocs.com/contact/16175551212' \
--header 'apikey: [your api key]'
```

+++
