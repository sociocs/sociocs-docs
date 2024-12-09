---
title: Delete scheduled message
order: -400
data:
    path: "/messages/scheduled/[message_id]"
    path_for_sample: "/messages/scheduled/Xyz12345"
---

Delete a scheduled message.

!!!warning
You cannot delete a scheduled message which is already being sent or is already sent.
!!!

## Method

[!badge DELETE]

## Path

`{{path}}`

## Path parameter

Name | Value | Required? {class="compact"}
--- | ---
message_id | ID of the scheduled message. | Yes

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
{{include "curl/delete"}}
```

+++
