---
title: Update contact
order: -400
---

Update a contact.

## Method

[!badge PUT]

## Path

`/contacts/[phone_number]`

## Path parameter

Name | Value | Required? {class="compact"}
--- | ---
phone_number | {{include "api/phone-number-value"}} | Yes

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
phone_number_cc | Phone number country dial code (e.g. "1") | String | No
name | Contact person name | String | No
extra_fields | {{include "api/contact-extra-fields-value"}} | Object | No

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
curl --location --request PUT 'https://api.sociocs.com/contact/16175551212' \
--header 'apikey: [your api key]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "John Davidson",
    "phone_number_cc": "1",
    "extra_fields": {
        "email_address": john@example.com
    }
}'
```

+++
