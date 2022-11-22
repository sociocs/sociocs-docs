---
label: Click to Chat by WhatsApp
title: "Bubble plugin :: Sociocs - Click to Chat by WhatsApp"
order: -200
---

## Introduction

This plugin adds a chat bubble on your website that draw user's attention, and gives them an easy way to reach out to you. It converts an inquiry into WhatsApp based conversation, so that your user doesn't have to wait on the website for a response.

When your web app user initiates the inquiry, it shows up in your Sociocs Inbox, from where you can reply to the user, and continue the conversation.

[!button variant="info" target="blank" text="Demo"](https://sociocs-plugins.bubbleapps.io/version-test/c2cwa_demo) [!button variant="info" target="blank" text="Plugin page on Bubble"](https://bubble.io/plugin/sociocs---click-to-chat-by-whatsapp-1649935178739x469570815670353900)

## Plugin Installation

1. In the Bubble dashboard, go to "*Plugins*".

1. Click on "*+ Add Plugins*".

1. Search for "*Sociocs - Click to Chat by WhatsApp*".

1. Click on "*Install*".

## Plugin Configuration

### Sociocs

{{include "signup-or-login"}}

1. Select "*WhatsApp (with Twilio)*" or "*WhatsApp (with Gupshup)*" in the "*Connect a new channel*" page. If you are an existing user, after logging in, click on "*Channels*" menu on the top, click on "*+*" button to go to the "*Connect a new channel*" page.

1. Finish the channel setup by following the instructions.

1. Go to "*Connect a new channel*" page again (click on "*Channels*" on the top menu, and click on "*+*" button), and select "*Click to Chat by WhatsApp*". Enter information and click "*Next*".

1. You should see a code sample, find these values in the code sample: "*data-channel*", and "*data-prompt-text*". These fields are referred without "*data-*" prefix in the below steps (e.g. "*data-channel*" is referred as "*channel*" etc.)
    ![image](https://user-images.githubusercontent.com/12301512/179740515-74bc9959-e04c-4ae0-85e9-87927223b5e2.png)

### Bubble Editor

1. Go to the "*Sociocs - Click to Chat by WhatsApp*" plugin in the Bubble Editor.

1. Add "*channel*", and "*prompt-text*" configuration parameters.

1. Bubble also shows fields for adding dev keys (i.e. "*channel - dev.*", and "*prompt-text - dev.*"). You can leave them blank.

That's it! Refresh your Bubble web app page, and you should see a chat bubble on bottom right.
