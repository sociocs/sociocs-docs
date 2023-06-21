---
title: Information
order: -100
---

Webhooks are the REST APIs you created yourself or offered by a third-party software, which get called when a message is received in a Sociocs channel.

URL of the REST API is referred to as webhook endpoint. You can set multiple webhooks endpoints for the same channel, or the same webhook endpoint for multiple channels.

!!!
As of now, Sociocs calls webhook only for "incoming" messages, that is, for the messages received from someone to your Sociocs connected channel.
!!!

## Channels supporting webhooks

- SMS (with Twilio)
- WhatsApp (with Gupshup)
- WhatsApp (with Twilio)

## How to set it up?

In order for Sociocs to start calling your webhook endpoint on receiving incoming messages, you need to subscribe the endpoint for a specific channel. You can add multiple webhooks for the same channel, or same webhook for multiple channels, depending upon your needs.

## Webhook endpoint invocation details

Sociocs calls the webhook endpoints with an assumption that it's a REST API accepting JSON body parameters.

### Method used

[!badge POST]

### Body parameters

Name | Value | Data type {class="compact"}
--- | ---
provider | `twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp) | String
channel_key | Channel key associated to the webhook | String
from | Sending phone number | String
to | Receiving phone number | String
name | Sender's name (if available) | String
text | Message text | String
image_url | Not available yet. Value is always empty. | -
image_urls | Not available yet. Value is always `null` | -
file_url | Not available yet. Value is always empty. | -
