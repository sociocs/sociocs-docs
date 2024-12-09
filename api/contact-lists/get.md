---
title: Get contact lists
order: -200
data:
    path: "/lists"
    path_for_sample: "/lists"
---

Get all the contact lists.

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
data | Array of contact list objects | Only present when status is `success`

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
