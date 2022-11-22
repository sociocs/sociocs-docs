---
label: Send Text Messages
title: "Bubble plugin :: Sociocs - Send Text Messages"
order: -400
---

!!!
This plugin itself is FREE, however, it requires a FREE TRIAL or PAID account on Sociocs to use the necessary API for this plugin.
!!!

## Introduction

This plugin allows sending text messages from your Bubble app.

Enable two-way conversations with your Bubble app users with the Sociocs inbox. For example, you send an order confirmation from your bubble app, which is also visible in your Sociocs inbox. When your user/customer replies to that message, it comes to the Sociocs inbox, from where you can reply back.

This plugin offers two actions, you can use either or both depending upon your use case.

1. *Send Sociocs Message* - To send outbound message.

1. *Save Sociocs Incoming* - To add an incoming message from your user/customer (e.g. a form submission or a simulated entry to save details which can be useful later.)

[!button variant="info" target="blank" text="Plugin page on Bubble"](https://bubble.io/plugin/sociocs---send-text-messages-1649178097706x937880861409017900)

## Supported channels

- SMS (with Twilio)
- WhatsApp (with Twilio)
- WhatsApp (with Gupshup)

## Plugin Installation

1. In the Bubble dashboard, go to "*Plugins*".

1. Click on "*+ Add Plugins*".

1. Search for "*Sociocs - Send Text Messages*".

1. Click on "*Install*".

## Plugin Configuration

### Sociocs

{{include "signup-or-login"}}

1. Connect "*SMS (with Twilio)*", "*WhatsApp (with Gupshup)*", or "*WhatsApp (with Twilio)*" channel on the "*Connect a new channel*" page. If you are an existing user, after logging in, click on "*Channels*" menu on the top, click on "*+*" button to go to the "*Connect a new channel*" page.

1. Go to "*Profile & settings -> API*".
    ![image](https://user-images.githubusercontent.com/12301512/163997321-90b286f5-e1aa-4df8-bc18-e453b20d26e8.png)

1. Find "*API Key*" (referred to as "*api_key*" in Bubble editor steps below). If you're using Sociocs API for the first time, you need to enable it by clicking on "*Enable API*" button.

1. Scroll down to code sample on the same page, and find values for these in the code sample: "*provider*", "*channel_key*".
    ![image](https://user-images.githubusercontent.com/12301512/163997897-82d5bf2a-80dc-4737-8188-2d7fca38feea.png)

### Bubble Editor

1. Go to the "*Sociocs - Send Text Messages*" plugin in the Bubble Editor.

1. Add "*api_key*", "*provider*", and "*channel_key*" parameters in the installed bubble plugin.

1. Bubble also shows fields for adding dev keys (i.e. "*api_key - dev.*", "*provider - dev.*", and "*channel_key - dev.*"). You can leave them blank.

## Bubble workflow setup

### Bubble Editor - Workflow tab/page

1. Add a new action at the step where you would like to send a message to the user.

1. **This is an optional step.** You can save certain information (e.g. order details) in Sociocs before a message is sent to a user/customer. This info could be useful when user/customer replies with questions. Your user/customer doesn't see or receive it. In Sociocs Inbox, this info shows as an incoming message from the user. You can skip to next step if you do not wish to save any details.
    a. In the action popup, select "*Save Sociocs Incoming*".
        ![image](https://user-images.githubusercontent.com/12301512/164000781-f074ecf0-314f-4e00-a1e9-37e03f51d15d.png)

    a. Enter the "*From*" (required), "*Name*" (optional) and "*Text*" (required) fields to use in all the actions or set them to use dynamic values.
        ![image](https://user-images.githubusercontent.com/12301512/164002625-f60d68fc-4531-4099-b3b6-a67766020551.png)

1. To send message to the user
    a. In the action popup, select "*Plugins -> Send Sociocs Message*".
    ![image](https://user-images.githubusercontent.com/12301512/163999772-ecc55862-0651-4a1f-afb4-9faf6a7fb867.png)

    a. Enter the "*To*" (required), "*Name*" (optional) and "*Text*" (required) fields to use in all the actions or set them to use dynamic values.
    ![image](https://user-images.githubusercontent.com/12301512/164008778-281afaa6-917a-49bb-a5ca-d6ce3c372708.png)

    a. You can also send images or a file to the user. If you will be using values from the database, ensure that either the "*Data type*" is publicly accessible, OR under "*Privacy*" tab, "*Everyone else*" has access to "*Find this in searches*" and image and/or file field.
        - To send one image, enter "*Image URL*" or set it to use a dynamic URL value.
        - To send multiple images, set "*Image URLs*" to use a dynamic URL values.
        - To send a file, enter "*File URL*" or set it to use a dynamic URL value. Support for file types in the SMS/MMS clients is very limited, so all your recipients may not be able to see/open the received file.
        ![image](https://user-images.githubusercontent.com/12301512/164025420-907402bd-61dd-4fdd-89bc-9ae5f9a75daa.png)

That's it, you are all set to send messages to you users!
