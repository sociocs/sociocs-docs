---
title: Is contact blocked
order: -800
---

Check if a contact is blocked.

## Method

[!badge GET]

## Path

`/contacts/isblocked/[phone_number]`

## Path parameter

Name | Value | Required? {class="compact"}
--- | ---
phone_number | {{include "api/phone-number-value"}} | Yes

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
status | `success` or `error` | -
errors | Array of object `{ msg: [error detail] }` | Only present when status is `error`
data | Object `{ is_blocked: true | false}` | Only present when status is `success`

## Code sample

+++ cURL

```shell
curl --location --request GET 'https://api.sociocs.com/contact/isblocked/16175551212' \
--header 'apikey: [your api key]'
```

+++
