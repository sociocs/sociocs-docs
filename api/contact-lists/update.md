---
title: Update contact list
order: -300
data:
    path: "/lists/[id]"
    path_for_sample: "/lists/10001"
---

Update an existing contact list.

## Method

[!badge PUT]

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
data | Object `{ id: [updated contact list's id]}` | Only present when status is `success`

## Code sample

+++ cURL

```shell
curl --location --request PUT '{{apiBaseUrl}}{{path_for_sample ?? path}}' \
{{include "curl/header-apikey"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "name": "My Contact List New Name"
}'
```

+++
