---
title: Send message
order: -300
---

- Send a message on Twilio SMS, Twilio WhatsApp or Gupshup WhatsApp channel.
- You can also send one or more images or a file.
- Optionally, you can also save recipient in a contact list.

## Method

[!badge POST]

## Path

`/messages`

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
provider | `twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp) | String | Yes
channel_key | Channel key value from *Profile & settings -> API* | String | Yes
to | {{include "api/phone-number-value"}} | String | Yes
name | Recipient name | String | No
text | Message text | String | No (when image_url, image_urls or file_url is present)
image_url | Publicly accessible image URL | String | No (when text, image_urls or file_url is present)
image_urls | Array of publicly accessible image URLs | String | No (when text, image_url or file_url is present)
file_url | Publicly accessible file URL | String | No (when text, image_url or image_urls is present)
contact_saving | Object with instruction to save phone number and name as a contact after sending the message. See below | Object | No

### contact_saving

This field is for passing instruction to save phone number and name as a contact. If the contact already exists, it will be updated. Extra custom fields can also be passed.

Name | Value | Data type | Required? {class="compact"}
--- | ---
save | `true` - Save phone number, name and extra fields as a contact, <br /> `false` - Skip saving as contact | Boolean | No (defaults to `false`)
list_id | {{include "api/contact-list-id-value"}} | Integer | No (defaults to `0`)
extra_fields | {{include "api/contact-extra-fields-value"}} | Object | No

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
status | `success` or `error` | -
errors | Array of object `{ msg: [error detail] }` | Only present when status is `error`

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

### Response object examples

#### When the API call was successful

```json
{
    "status": "success"
}
```

#### When the API call was unsuccessful

```json
{
    "status": "error",
    "errors": [{ "msg": "Invalid channel_key." }]
}
```
