---
title: Unblock contact
order: -700
---

Unblock bulk & automated messages to a contact.

## Method

[!badge POST]

## Path

`/contacts/unblock/[phone_number]`

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

## Code sample

+++ cURL

```shell
curl --location --request POST 'https://api.sociocs.com/contact/unblock/16175551212' \
--header 'apikey: [your api key]'
```

+++
