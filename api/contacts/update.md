---
title: Update contact
order: -400
data:
    path: "/contacts/[phone_number]"
    path_for_sample: "/contacts/16175551212"
---

Update a contact.

## Method

[!badge PUT]

## Path

`{{path}}`

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

Name | Value | Remarks {class="compact"}
--- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}

## Code sample

+++ cURL

```shell
curl --location --request PUT '{{apiBaseUrl}}{{path_for_sample ?? path}}' \
{{include "curl/header-apikey"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "name": "John Davidson",
    "phone_number_cc": "1",
    "extra_fields": {
        "email_address": john@example.com
    }
}'
```

+++
