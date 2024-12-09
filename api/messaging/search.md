---
title: Search messages
order: -900
data:
    path: "/messages/search"
    path_for_sample: "/messages/search?text=interested"
---

Get all the unreplied messages.

## Method

[!badge GET]

## Path

`{{path}}`

## Query string parameter

Name | Value | Required? | Remarks {class="compact"}
--- | ---
text | Search term | Yes | -
direction | `incoming` (Search incoming messages only), <br />`outbound` (Search outgoing messages only), <br />`both` (Search all messages) | No |  Defaults to `both`
start_date | Date in YYYY-MM-DD format (e.g., `2024-01-01`) | No |  Defaults to 90 days before today. <br />Results include given date.
end_date | Date in YYYY-MM-DD format (e.g., `2024-01-31`) | No |  Defaults to today. <br />Results include given date.

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Array of message objects | Only present when status is `success`

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
