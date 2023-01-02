---
label: Click to Chat by Text
title: 'WordPress :: Sociocs - Click to Chat by Text/SMS'
order: -100
---

## Introduction

Sociocs Web Chat plugin adds a chat bubble on your website that draw user's attention, and gives them an easy way to reach out to you. It converts an inquiry into SMS / text messaging based conversation, so that your user doesn't have to wait on the website for a response.

When your web app user initiates the inquiry, it shows up in your Sociocs Inbox, from where you can reply to the user, and continue the conversation.

[!button variant="info" target="blank" text="Demo"](https://wordpress-demo.sociocs.com/)

![image](https://user-images.githubusercontent.com/12301512/203017406-4b197d3f-6094-496d-a76c-f84a0865c783.png)

## Setup

### Twilio

{{include "twilio-signup-steps"}}

### Sociocs

{{include "c2csms-channel-initial-steps"}}

1. You should see the plugin code. You will be using this code in your WordPress site in the instruction below.

### WP Admin Dashboard

Adding this plugin on a WordPress site simply requires inserting plugin script and div tag in your website. There are multiple ways to introduce custom JavaScript and HTML in a WordPress site. Here are the steps using a well known plugin `Insert Headers and Footers`.

#### Insert plugin script and div tag

1. Install "*Insert Headers and Footers*" plugin "*By WPBeginner*" through the "*Plugins*" menu in your admin dashboard.

2. Activate the plugin.

3. Go to the "Settings > Insert Headers and Footers" menu.

4. Copy and paste plugin code mentioned above in the "Scripts in Footer" textbox.

5. Click "Save".

That's it! Refresh your WordPress website page, and you should see a chat bubble on bottom right.
