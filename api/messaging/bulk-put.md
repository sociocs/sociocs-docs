---
title: Reschedule bulk messaging job
order: -700
data:
    path: "/messages/bulk/[job_id]"
    path_for_sample: "/messages/bulk/Xyz12345"
---

Reschedule a bulk messaging job.

!!!warning
You cannot update a bulk messaging job which is already executing or has already executed.
!!!

## Method

[!badge PUT]

## Path

`{{path}}`

## Path parameter

Name | Value | Required? {class="compact"}
--- | ---
job_id | ID of the scheduled job | Yes

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
schedule | ISO 8601 date & time (e.g., "2006-01-02T15:04:05-04:00"). If the value is in the past, messages will be sent immediately. | String | No

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Object `{ job_id: [bulk messaging job id] }` | Only present when status is `success`.

## Code sample

```shell
curl --location --request POST '{{apiBaseUrl}}{{path_for_sample ?? path}}' \
{{include "curl/header-apikey"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "schedule: "2023-12-25T11:00:00-04:00"
}'
```