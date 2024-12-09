---
title: Delete contact list
order: -400
data:
    path: "/lists/[id]"
    path_for_sample: "/lists/10001"
---

Delete an existing contact list.

## Method

[!badge DELETE]

## Path

`{{path}}`

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

| Name | Value | Remarks {class="compact"} |
| ---- | ----- |
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Object `{ id: [deleted contact list's id]}` | Only present when status is `success`

## Code sample

+++ cURL

```shell
{{include "curl/delete"}}
```

+++
