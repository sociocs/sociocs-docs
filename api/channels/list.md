---
title: Get channels
order: -100
---

Get the list of channels for the given provider.

## Method

[!badge GET]

## Path

`/channels`

## Query string parameter

Name | Value | Required? {class="compact"}
--- | ---
provider | `twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp) | Yes

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Array of object

Name | Value | Remarks {class="compact"}
--- | --- | ---
id | Channel ID | -
channel_key | Channel key | This is the same as the id field.
name | Channel name | -

## Code sample

+++ cURL

```shell
curl --location --request GET 'https://api.sociocs.com/channels?provider=twlo' \
--header 'apikey: [your api key]'
```

+++
