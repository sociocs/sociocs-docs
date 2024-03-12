---
label: Send WhatsApp Message Button
title: "Send WhatsApp Message Button"
order: -300
---

## Introduction

You can send ad-hoc WhatsApp messages to your contacts directly from ActiveCampaign contact details page after you install our Chrome extension.

!!!
This feature is available for both the FREE and PAID accounts.
!!!

[!badge size="xl" target="blank" text="Get Chrome extension" icon="link-external" iconAlign="right"](https://chromewebstore.google.com/detail/send-whatsapp-messsages-f/mlicpgdipoofkbcanbkbfipgbldiebic)

## Supported channels

- WhatsApp (with Twilio)
- WhatsApp (with Gupshup)

## Setup on Sociocs

{{include "signup-or-login"}}

1. Connect "*WhatsApp (with Gupshup)*", or "*WhatsApp (with Twilio)*" channel on the "*Connect a new channel*" page. If you're an existing user, after logging in, click on "*Channels*" menu on the top, click on "*+*" button to go to the "*Connect a new channel*" page.

## Install the Chrome extension

1. Go to the <a href="https://chromewebstore.google.com/detail/send-whatsapp-messsages-f/mlicpgdipoofkbcanbkbfipgbldiebic" target="_blank">Chrome extension page</a>.

1. Click on "*Add to Chrome*".

1. You will get a warning popup like below. Click on "*Add extension*".
    ![Chrome Extension Installation Warning](https://github.com/sociocs/docs/assets/12301512/8755512e-53e5-41e5-826f-f054f548cf28)

## Use it on ActiveCampaign

1. Go to contact details page on ActiveCampaign.

1. You should see a WhatsApp icon button next to the phone number. Click on the icon which opens the Sociocs Outbound Compose page.
    ![WhatsApp Icon Button](https://github.com/sociocs/docs/assets/12301512/65f3705d-ca4d-4919-aff2-911e8b3f94df)

1. Enter "*Message text*" (with personalization if you like), and click "*Send*". Below [!badge text="dynamic fields" target="_blank"](/miscellaneous/dynamic-fields.md) supported on the Compose page with this feature.

    Dynamic field | Remarks {class="compact"}
    --- | ---
    \{\{BUSINESS_NAME\}\} | Your business name.
    \{\{CUSTOMER_NAME\}\} | Name of the recipient.
    \{\{FIRST_NAME\}\} | First name of the recipient.
    \{\{LAST_NAME\}\} | Last name of the recipient.
    \{\{PHONE_NUMBER\}\} | Phone number of the recipient starting with the country dial code (e.g., 16317471111).
    \{\{SENDER_NAME\}\} | Name of the person sending the bulk messages.

{{include "alert-whatsapp-apprvd-tmplt-reqd"}}
