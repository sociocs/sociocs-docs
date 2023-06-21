---
title: Get channels
order: -100
---

Gets the list of channels for the given provider.

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

Name | Value {class="compact"}
--- | ---
id | Channel ID
name | Channel name

## Code sample

+++ cURL

```shell
curl --location --request GET 'https://api.sociocs.com/channels?provider=twlo' \
--header 'apikey: [your api key]'
```

+++
