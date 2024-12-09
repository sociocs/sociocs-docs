---
title: Add contacts to list
order: -900
data:
    path: /contacts/add-to-list
    path_for_sample: /contact/add-to-list
---

Add one or more contacts to a contact list using phone numbers.

## Method

[!badge POST]

## Path

`{{path}}`

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
dest_list_id | Destination contact list ID | Integer | Yes
phone_numbers | Array of the phone numbers of the contacts to be added to the list (e.g. `["16317471111"]`) | Array of string | Yes

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
{{include "curl/post"}}
{{include "curl/header-ct-json"}} \
--data-raw '{
    "dest_list_id": 10001,
    "phone_numbers": ["16317471111", "16317472222"]
}'
```

+++
