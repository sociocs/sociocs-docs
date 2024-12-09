---
title: Get scheduled messages
order: -300
data:
    path: "/messages/scheduled"
---

Get the list of scheduled messages. The list will have max 100 records, ordered by the scheduled date in descending order. Pagination is not available at the moment.

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
data | Array of object with the scheduled message fields. | Only present when status is `success`.

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
