---
title: Unsubscribe
order: -500
data:
    path: "/webhook-subscriptions/[subscription_id]"
    path_for_sample: "/webhook-subscriptions/ABC1234567890XYZ"
---

Unsubscribe a webhook to stop receiving messages.

## Method

[!badge DELETE]

## Path

`{{path}}`

## Path parameter

Name | Value | Required? {class="compact"}
--- | ---
subscription_id | Subscription ID | Yes

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
