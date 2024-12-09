---
title: Delete bulk messaging job
order: -800
data:
    path: "/messages/bulk/[job_id]"
    path_for_sample: "/messages/bulk/Xyz12345"
---

Delete a bulk messaging job.

!!!warning
You cannot delete a bulk messaging job which is already executing or has already executed.
!!!

## Method

[!badge DELETE]

## Path

`{{path}}`

## Path parameter

Name | Value | Required? {class="compact"}
--- | ---
job_id | ID of the scheduled bulk messaging job. | Yes

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
