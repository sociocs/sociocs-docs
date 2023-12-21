---
title: Add contacts bulk
order: -200
data:
    path: "/contacts/bulk"
---

Add new contacts in bulk. When a given phone number already exists, it updates existing contact. If existing contact gets updated, all information gets overwritten, including all extra fields.

## Method

[!badge POST]

## Path

`{{path}}`

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
list_id | {{include "api/contact-list-id-value"}} | Integer | No (defaults to 0)
phone_number_cc | Phone number country dial code (e.g. "1") | String | No
records | See below | Array | Yes

### records

The 'records' field is supposed to be an array of **up to 10,000** contacts. Each item in the array should be as below.

Name | Value | Data type | Required? {class="compact"}
--- | ---
phone_number | {{include "api/phone-number-value"}} | String | Yes
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

## Code sample

+++ cURL

```shell
curl --location --request POST '{{apiBaseUrl}}{{path_for_sample ?? path}}' \
{{include "curl/header-apikey"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "list_id": 0,
    "phone_number_cc": "1",
    "records": [
        {
            "phone_number": "16175551212",
            "name": "John Johnson",
            "extra_fields": {
                "email_address": john@example.com
            }
        },
        {
            "phone_number": "16175551111",
            "name": "David Davidson",
            "extra_fields": {
                "email_address": david@example.com
            }
        }
    ]
}'
```

+++
