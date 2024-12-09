---
title: Create contact list
order: -100
data:
    path: "/lists"
    path_for_sample: "/lists"
---

Create a new contact list.

## Method

[!badge POST]

## Path

`{{path}}`

## Body parameters

| Name | Value             | Data type | Required? {class="compact"} |
| ---- | ----------------- |
| name | Contact list name | String    | Yes                         |

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

| Name | Value | Remarks {class="compact"} |
| ---- | ----- |
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Object `{ id: [new contact list id]}` | Only present when status is `success`

## Code sample

+++ cURL

```shell
curl --location --request POST '{{apiBaseUrl}}{{path_for_sample ?? path}}' \
{{include "curl/header-apikey"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "name": "My Contact List"
}'
```

+++
