---
label: Sociocs - "Live Chat" by Text
title: 'Bubble plugin :: Sociocs - "Live Chat" by Text'
order: -300
---

## Introduction

This plugin adds a chat bubble on your website that draw user's attention, and gives them an easy way to reach out to you. It converts the inquiries into SMS / text messaging based conversation, so that your user doesn't have to wait on the website for a response.

When your web app user initiates the inquiry, it shows up in your Sociocs Inbox, from where you can reply to the user, and continue the conversation.

[!button variant="info" target="blank" text="Demo"](https://sociocs-plugins.bubbleapps.io/version-test/live_chat_by_text_demo) [!button variant="info" target="blank" text="Plugin page on Bubble"](https://bubble.io/plugin/sociocs---live-chat-by-text-1649745550565x177374092711165950)

## Plugin Installation

1. In the Bubble dashboard, go to "*Plugins*".

1. Click on "*+ Add Plugins*".

1. Search for 'Sociocs - "*Live Chat*" by Text'.

1. Click on "*Install*".

## Plugin Configuration

### Twilio

* You can skip this step if you already have an account with Twilio.
* If you don't have an account with Twilio, you can sign up for a [free trial account](https://www.twilio.com/referral/ExBdSZ). (Once you sign up using our link, you should consider upgrading right away to receive a FREE $10 credit.)

### Sociocs

1. Sign up or login on <a href="https://app.sociocs.com" target="_blank">app.sociocs.com</a>.

1. Select "*SMS (with Twilio)*" in the "*Connect a new channel*" page. If you are an existing user, after logging in, click on "*Channels*" menu on the top, click on "*+*" button to go to the "*Connect a new channel*" page.

1. Finish the channel setup by following the instructions.

1. Go to "*Connect a new channel*" page again (click on "*Channels*" on the top menu, and click on "*+*" button), and select "*Click to Chat by Text/SMS*". Enter information and click "*Next*".

1. You should see a code sample, find these values in the code sample: "*data-channel*", "*data-primary-color*", and "*data-prompt-text*". These fields are referred without "*data-*" prefix in the below step (e.g. "*data-channel*" is referred as "*channel*" etc.)
    ![image](https://user-images.githubusercontent.com/12301512/179742406-bbf28620-0024-44da-b532-4155fca6829f.png)

### Bubble Editor

1. Go to the "*Sociocs - Click to Chat by WhatsApp*" plugin in the Bubble Editor.

1. Add "*channel*", "*primary-color*", and "*prompt-text*" configuration parameters.

1. Bubble also shows fields for adding dev keys (i.e. "*channel - dev.*", "*primary-color - dev.*", and "*prompt-text - dev.*"). You can leave them blank.

That's it! Refresh your Bubble web app page, and you should see a chat bubble on bottom right.
