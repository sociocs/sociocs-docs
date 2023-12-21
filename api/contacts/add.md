---
title: Add contact
order: -100
data:
    path: "/contacts/[phone_number]"
    path_for_sample: "/contacts/16175551212"
---

Add a new contact. When a given phone number already exists, it updates existing contact. If existing contact gets updated, all information gets overwritten, including all extra fields.

## Method

[!badge POST]

## Path

`{{path}}`

## Path parameter

Name | Value | Required? {class="compact"}
--- | ---
phone_number | {{include "api/phone-number-value"}} | Yes

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
list_id | {{include "api/contact-list-id-value"}} | Integer | No (defaults to 0)
phone_number_cc | Phone number country dial code (e.g. "1") | String | No
name | Contact person name | String | No
extra_fields | {{include "api/contact-extra-fields-value"}} | Object | No

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Object `{ id: [new contact id]}` | Only present when status is `success`

## Code sample

+++ cURL

```shell
curl --location --request POST '{{apiBaseUrl}}{{path_for_sample ?? path}}' \
{{include "curl/header-apikey"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "list_id": 0,
    "phone_number_cc": "1",
    "name": "John Johnson",
    "extra_fields": {
        "email_address": john@example.com
    }
}'
```

+++
