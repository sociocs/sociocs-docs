---
label: ActiveCampaign
title: "ActiveCampaign app :: Sociocs"
order: -100
---

## Introduction

This app adds ability for you to send text/SMS (using your Twilio account) or WhatsApp messages (using your Twilio or Gupshup account) from your ActiveCampaign automation.

When the recipient replies to the message, it shows up in your Sociocs Inbox, from where you can reply, and continue the conversation.

!!!
If you're already using Twilio app in ActiveCampaign for sending SMS, you can replace it with the Sociocs app to enable a two-way conversation with the recipients.
!!!

!!!
You need a FREE TRIAL or PAID account on Sociocs to use the necessary API for this app.
!!!

[!button variant="info" target="blank" text="App page on ActiveCampaign"](https://www.activecampaign.com/apps/sociocs-integration)

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

1. Find "*API key*". You'll need it later. (If you're using Sociocs API for the first time, you need to enable it by clicking on "*Enable API*" button.)

## Setup on ActiveCampaign

### Add the ActiveCampaign "Action"

#### Option 1

1. In your ActiveCampaign automation, Click on the "*+*" button to add a new action.

1. In the resulting popup, click on "*CX Apps*" on the left sidebar.

1. Look for "*Sociocs - Send Message*" in the result, and click on it.

#### Option 2

1. In your ActiveCampaign automation, search for *Sociocs - Send Message* in the right sidebar.

1. Drag and drop the "*Sociocs - Send Message*" action at an appropriate step in your automation.

### Connect your Sociocs Account

1. Once you add the action, a popup opens up.

1. Paste the Sociocs "*API key*".

1. Click "*Connect*".

![Connect](https://github.com/sociocs/docs/assets/12301512/d9a31e0a-08f0-45ef-9202-156682f9530e)

### Complete the Message Sending setup

1. Once you connect your Sociocs account, you should see a second step named "Setup"

1. Select "*Provider*" depending upon the type of the channel you added on Sociocs. For example, if you added the "*SMS (with Twilio)*" channel on Sociocs, you should select "Twilio SMS" in the dropdown list.

1. Select "*Channel*" depending upon the phone number you would like to use for sending messages. If you have only one channel on Sociocs, you should see only one option in the dropdown list.

1. Enter "*Message text*" (with personalization if you like), and click "*Finish*".
    !!!warning
    If you're using a WhatsApp channel, make sure the message text is approved as a template by WhatsApp, and enter it exactly as the approved template's text.

    You can submit the template for approval on the website of the provider you used (e.g., Twilio) for creating your WhatsApp account.
    !!!

![image](https://github.com/sociocs/docs/assets/12301512/c5ddc3ba-8e6d-4db8-a637-8082e53da84f)

*That's it, you are all set to send messages to your target recipients!*
