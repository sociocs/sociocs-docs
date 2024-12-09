---
title: Get bulk messaging jobs
order: -600
data:
    path: "/messages/bulk"
    path_for_sample: "/messages/bulk"
---

Get the list of bulk messaging jobs. The list will have max 100 records, ordered by the scheduled date in descending order. Pagination is not available at the moment.

## Method

[!badge GET]

## Path

`{{path}}`

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Array of object with the bulk messaging job fields. | Only present when status is `success`.

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
