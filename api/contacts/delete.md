---
title: Delete contact
order: -500
data:
    path: "/contacts/[phone_number]"
    path_for_sample: "/contacts/16175551212"
---

Delete a contact.

## Method

[!badge DELETE]

## Path

`{{path}}`

## Path parameter

Name | Value | Required? {class="compact"}
--- | ---
phone_number | {{include "api/phone-number-value"}} | Yes

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
list_id | 0 - to delete the contact (including from all the contact lists) or <br/> List ID - to delete only from a contact list (List ID is the value shown in the address bar when a list is selected on the Contacts page)  | Integer | No (defaults to 0)

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
curl --location --request DELETE '{{apiBaseUrl}}{{path_for_sample ?? path}}' \
{{include "curl/header-apikey"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "list_id_": 0
}'
```

+++
