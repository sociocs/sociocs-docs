---
title: Get channel
order: -200
---

Gets a channel.

## Method

[!badge GET]

## Path

`/channels/[channel_key]`

## Path parameter

Name | Value | Required? {class="compact"}
--- | ---
channel_key | Channel key value from Profile & settings -> API | Yes

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
status | `success` or `error` | -
errors | Array of object `{ msg: [error detail] }` | Only present when status is `error`
data | Channel object | Only present when status is `success`

#### Channel object

Name | Value {class="compact"}
--- | ---
name | Channel name
country_code | Country dial code of the phone number connected in the channel
phone_number | Phone number connected in the channel
provider | Messaging provider for the channel <br />{{include "providers"}}
