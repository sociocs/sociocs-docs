---
title: Move contacts to list
order: -1000
data:
    path: /contacts/move-to-list
    path_for_sample: /contacts/move-to-list
---

Move one or more contacts from one contact list to another using phone numbers.

## Method

[!badge POST]

## Path

`{{path}}`

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
source_list_id | Source contact list ID | Integer | Yes
dest_list_id | Destination contact list ID | Integer | Yes
phone_numbers | Array of the phone numbers of the contacts to be moved (e.g. `["16317471111"]`) | Array of string | Yes

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
    "source_list_id": 10001,
    "dest_list_id": 10002,
    "phone_numbers": ["16317471111", "16317472222"]
}'
```

+++
