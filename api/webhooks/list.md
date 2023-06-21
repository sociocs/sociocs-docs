---
title: Get subscriptions
order: -300
data:
    path: "/webhook-subscriptions"
---

Get the list of subscriptions.

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
data | Array of subscription object. See below | Only present when status is `success`

#### Subscription object

{{include "subscription-object-table"}}

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
