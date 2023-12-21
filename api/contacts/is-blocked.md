---
title: Is contact blocked
order: -800
data:
    path: /contacts/isblocked/[phone_number]
    path_for_sample: /contact/isblocked/16175551212
---

Check if a contact is blocked.

## Method

[!badge GET]

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
data | Object `{ is_blocked: true | false}` | Only present when status is `success`

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
