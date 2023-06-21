---
title: Save incoming message
order: -200
---

Save a message in the inbox. You can use it to save a message received on an external platform or create a mock message with information you may need during the conversation.

## Method

[!badge POST]

## Path

`/incoming`

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
provider | `twlo` (for Twilio SMS). No other providers supported yet. | String | Yes
channel_key | Channel key value from *Profile & settings -> API*  | String| Yes
from | {{include "api/phone-number-value"}} | String | Yes
name | Sender name | String | No
text | Message text | String | Yes

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
status | `success` or `error` | -
errors | Array of object `{ msg: [error detail] }` | Only present when status is `error`

## Code sample

+++ cURL

```shell
curl --location --request POST 'https://api.sociocs.com/incoming' \
--header 'apikey: [your api key]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "provider": "[provider]",
    "channel_key": "[your channel key]",
    "from": "[phone number]",
    "name": "[sender name]",
    "text": "[message]"
}'
```

+++
