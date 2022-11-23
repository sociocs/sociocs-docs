---
title: Send message
order: -200
---

Send a message on Twilio SMS, Twilio WhatsApp or Gupshup WhatsApp channel. You can also send one or more images or a file.

## Method

[!badge POST]

## Path

`/message`

## Body parameters

Name | Value | Required? {class="compact"}
--- | ---
provider | `twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp) | Yes
channel_key | Channel key value from *Profile & settings -> API* | Yes
to | Phone number in E. 164 format e.g. +16175551212 | Yes
name | Customer name | No
text | Message text | No (when image_url, image_urls or file_url is present)
image_url | Publicly accessible image URL | No (when text, image_urls or file_url is present)
image_urls | Array of publicly accessible image URLs | No (when text, image_url or file_url is present)
file_url | Publicly accessible file URL | No (when text, image_url or image_urls is present)

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Description {class="compact"}
--- | ---
status | `success` or `error` | -
errors | Array of map `{ msg: [error detail] }` | Only present when status is `error`

## Code samples

### Sending only text content

+++ cURL

```shell
curl --location --request POST 'https://api.sociocs.com/message' \
--header 'apikey: [your api key]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "provider": "[provider]",
    "channel_key": "[your channel key]",
    "to": "[phone number]",
    "name": "[recipient name]",
    "text": "[message]"
}'
```

+++

### Sending text & image

+++ cURL

```shell
curl --location --request POST 'https://api.sociocs.com/message' \
--header 'apikey: [your api key]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "provider": "[provider]",
    "channel_key": "[your channel key]",
    "to": "[phone number]",
    "name": "[recipient name]",
    "text": "[message]",
    "image_url": "[image url]"
}'
```

+++

### Sending only images

+++ cURL

```shell
curl --location --request POST 'https://api.sociocs.com/message' \
--header 'apikey: [your api key]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "provider": "[provider]",
    "channel_key": "[your channel key]",
    "to": "[phone number]",
    "name": "[recipient name]",
    "image_urls": [
        "[image url 1]",
        "[image url 2]",
        "[image url 3]"
    ]
}'
```

+++
