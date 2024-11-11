---
title: Get team members
order: -100
data:
    path: "/team-members"
    path_for_sample: "/team-members"
---

Get the list of all the team members.

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
data | Object with the team member fields | Only present when status is `success`

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
