---
label: Keap
title: "Keap integration with Sociocs"
order: -250
---

## Introduction

Add ability to send text/SMS (using your Twilio account) or WhatsApp messages (using your Twilio or Gupshup account) from your Keap automation.

When the recipient replies to the message, it shows up in your Sociocs Inbox, from where you can reply, and continue the conversation.

!!!
If you're already using Twilio API under "Send HTTP Post" in Keap for sending SMS, you can replace it with the Sociocs app to enable a two-way conversation with the recipients.
!!!

!!!
You need a FREE TRIAL or PAID account on Sociocs to use the necessary API for this integration.
!!!

## Supported channels

- SMS (with Twilio)
- WhatsApp (with Twilio)
- WhatsApp (with Gupshup)

## Setup on Sociocs

{{include "signup-or-login"}}

1. Connect "*SMS (with Twilio)*", "*WhatsApp (with Gupshup)*", or "*WhatsApp (with Twilio)*" channel on the "*Connect a new channel*" page. If you're an existing user, after logging in, click on "*Channels*" menu on the top, click on "*+*" button to go to the "*Connect a new channel*" page.

1. Go to "*Profile & settings -> API*".
    ![settings](https://user-images.githubusercontent.com/12301512/163997321-90b286f5-e1aa-4df8-bc18-e453b20d26e8.png)

    ![api](https://github.com/sociocs/docs/assets/12301512/4168b133-c8e2-4834-9b7b-d62b5203349c)

1. Find "*API key*", "*provider*", and "*channel_key*". You'll need this information later. (If you're using Sociocs API for the first time, you need to enable it by clicking on "*Enable API*" button.)
    ![key](https://github.com/sociocs/docs/assets/12301512/0e760d3f-fbae-4588-a045-21b8ea812a60)

## Setup on Keap

1. Open the automation sequence where you want to add the SMS message.
    ![sequence](https://github.com/sociocs/docs/assets/12301512/4272790c-5d50-46f6-a5ed-683a3a7feda1)

1. Drag an HTTP Post object onto the canvas.
    ![post](https://github.com/sociocs/docs/assets/12301512/a3e29184-ba66-4a77-9198-e49a4e147720)

1. Double click the added HTTP Post action to edit it.

1. Under "*POST URL*", enter Sociocs API URL with your API key in below format.
    `https://api.sociocs.com/message?apikey=your-api-key`

    For example, if you API key is `abcd1234`, the API URL value should be entered as `https://api.sociocs.com/message?apikey=abcd1234`

1. Under "Name / Value Pairs", enter below name and value pairs.

    Name | Value | Remarks {class="compact"}
    --- | --- | ---
    provider | provider value from "*Profile & settings -> API*" page (e.g., `twlo`) | If you've multiple phone numbers in Sociocs, make sure to select the applicable channel on the API page.
    channel_key | channel_key value from "*Profile & settings -> API*" page (e.g., `twlo_16317471111`) | If you've multiple phone numbers in Sociocs, make sure to select the applicable channel on the API page.
    to | `~Contact.Phone1~` | Recipient's phone number. You can also enter a phone number directly or use any other variable available in Keap.
    name | `~Contact.FirstName~` | Recipient's name. You can also enter a name directly or use any other variable available in Keap.
    text | `Hello world!` | SMS / text message content you would like to send.

    **Example:** ![pairs](https://github.com/sociocs/docs/assets/12301512/ffd6e34b-6e04-407e-95dd-bae092ded696)

1. Once you've got it all set up, you can quickly test it on your user record (assuming you've your mobile phone as the Phone 1 in your user record.)

    ![test](https://github.com/sociocs/docs/assets/12301512/685ae2df-fbde-47cc-b01e-9efbe293b318)

*That's it, you are all set to send messages to your target recipients!*
