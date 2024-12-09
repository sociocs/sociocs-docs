---
title: Block contact
order: -600
data:
    path: /contacts/block/[phone_number]
    path_for_sample: /contacts/block/16175551212
---

Block bulk & automated messages to a contact. Incoming messages are not blocked.

## Method

[!badge POST]

## Path

`{{path}}`

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
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}

## Code sample

+++ cURL

```shell
{{include "curl/post"}}
```

+++
