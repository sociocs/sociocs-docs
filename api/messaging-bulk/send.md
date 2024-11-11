---
title: Send bulk messages
order: -100
data:
    path: "/messages/bulk"
---

- Send messages in bulk on Twilio SMS, Twilio WhatsApp or Gupshup WhatsApp channel.
- You can also send an image, a video or a file.
- Calling this API will create a bulk messaging job, which you can also see and update on app.sociocs.com -> Bulk messaging -> History.

## Method

[!badge POST]

## Path

`{{path}}`

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
provider | `twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp) | String | Yes
channel_key | Channel key value from *Profile & settings -> API* | String | Yes
recipients | Array of object `{to: "phone_number", name: "recipient_name"}` | String | Yes
text | Message text | String | No (when image_url, image_urls or file_url is present)
image_url | Publicly accessible image URL | String | No (when text, video_url or file_url is present)
video_url | Publicly accessible video URL | String | No (when text, image_url or file_url is present)
file_url | Publicly accessible file URL | String | No (when text, image_url or video_url is present)
duplicates_allowed | `true` - Send message to duplicate phone numbers (if there are any), <br /> `false` - Send message only once per phone number (first occurrence) | Boolean | No (defaults to false)
schedule | ISO 8601 date & time (e.g., "2006-01-02T15:04:05-04:00"). If the value is in the past, messages will be sent immediately. | String | No
user_id | Sociocs user ID to show as sender of the message. When not provided, message is show as sent by `Sociocs API`. Use [/team-members](/api/team-members/list.md) endpoint to find out User IDs. | String | No

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Object `{ job_id: [bulk messaging job id] }` | Only present when status is `success`.

## Code sample

```shell
curl --location --request POST '{{apiBaseUrl}}{{path_for_sample ?? path}}' \
{{include "curl/header-apikey"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "provider": "twlo",
    "channel_key": "your_channel_key",
    "recipients": [
        {
            "to": "phone_number_1",
            "name": "recipient_name_1"
        },
        {
            "to": "phone_number_2",
            "name": "recipient_name_2"
        }
    ],
    "text": "message",
    "schedule: "2023-12-25T11:00:00-04:00"
}'
```