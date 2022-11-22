---
title: Save incoming message
order: -300
---

Save a message in the inbox. You can use it to save a message received on an external platform or create a mock message with information you may need during the conversation.

## Method

[!badge POST]

## Path

`/incoming`

## Body parameters

Name | Value | Required? {class="compact"}
--- | ---
provider | `twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp) | Yes
channel_key | Channel key value from *Profile & settings -> API* | Yes
from | Phone number in E. 164 format e.g. +16175551212 | Yes
name | Customer name | No
text | Message text | Yes

## Response

Name | Value | Description {class="compact"}
--- | ---
status | `success` or `error` | -
errors | Array of map `{ msg: [error detail] }` | Only present when status is `error`

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
