---
title: Get subscription
order: -400
data:
    path: "/webhook-subscriptions"
    path_for_sample: "/webhook-subscriptions/ABC1234567890XYZ"
---

Get a subscription.

## Method

[!badge GET]

## Path

`{{path}}/[subscription_id]`

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
data | Subscription object. See below | Only present when status is `success`

#### Subscription object

{{include "subscription-object-table"}}

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
