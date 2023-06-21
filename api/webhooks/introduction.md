---
title: Introduction
order: -100
---

Webhooks are the REST APIs you created yourself or offered by a third-party software, which get called when a message is received in a Sociocs channel.

URL of the REST API is referred to as webhook endpoint. You can set multiple webhooks endpoints for the same channel, or the same webhook endpoint for multiple channels.

!!!
As of now, Sociocs calls webhook only for "incoming" messages, that is, for the messages received from someone on your channel.
!!!

## Channels supporting webhooks

- SMS (with Twilio)
- WhatsApp (with Gupshup)
- WhatsApp (with Twilio)

## How to set it up?

In order for Sociocs to start calling your webhook endpoint on receiving incoming messages, you need to subscribe the endpoint for a specific channel. You can add multiple webhooks for the same channel, or same webhook for multiple channels, depending upon your needs.
