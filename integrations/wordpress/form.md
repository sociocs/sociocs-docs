---
label: Form
title: "WordPress :: Sociocs - Form"
order: -200
---

## Introduction

Form integration (e.g. Contact Us, Appointment Request, Pricing Inquiry form etc.) for WordPress.

When the end user submits the form, it is received in the Sociocs Inbox, form where, you can reply back.

[!button variant="info" target="blank" text="Demo"](https://wordpress-demo.sociocs.com/contact-us-demo/)

## Setup

!!!
There are different ways (with and without plugins) to create forms on WordPress, and have them submitted to an API. This guide is based on the well known form plugin `Contact Form 7` to create the form, and another plugin `Contact Form to Any API` to submit it to Sociocs API.
!!!

### Sociocs

{{include "form-channel-initial-steps"}}

1. Enter "*Form name*", check "*Key authorization*", and click "*Next*". **You don't need to add fill out any other information.** (Even if you would like to add "*reCAPTCHA*" validation in your form, leave "*reCAPTCHA v2*" unchecked in Sociocs. You would have to use Contact Form 7's reCAPTCHA integration.)
    ![image](https://user-images.githubusercontent.com/12301512/210250674-3371f72c-ad86-4a5b-a3c5-00bda432c769.png)

1. On the next page, click "*Done*", which should take you to the Channels page.

1. Click on the "*Form*" channel you just added, and find API URL, and API KEY (value shown under "*Key authorization*").
    ![image](https://user-images.githubusercontent.com/12301512/210251544-1218ad9b-e4e4-44c3-b854-11bf2e3a276b.png)

### WP Admin Dashboard

#### Create a form using Contact Form 7

Install "*Contact Form 7*" plugin through the "*Plugins*" menu in your admin dashboard. Create a form, and add it to a page on your website. Contact Form 7 documentation is available <a href="https://contactform7.com/docs/" target="_blank">here</a>.

#### Direct form submissions to Sociocs API

1. Install "*Contact Form to Any API*" plugin through the "*Plugins*" menu in your admin dashboard.

1. Go to "*CF7 to API*" from the menu, and click on "*Add New CF7 API*".

1. Fill the API information as explained below:

    Field | Value
    --- | ---
    Title | Name for this API entry. e.g. "Contact us form to Sociocs"
    Select Contact Form | Select your Contact Form 7 form
    API Url | Above mentioned API URL from Sociocs
    Header Request | Add above mentioned API Key in this format `apikey: your-api-key`
    Input Type | Parameters - GET/POST
    Method | POST
    Map your Fields | Email address field value must be `email`. Submitter name field value, if present, should be `name`. Other field values can be anything, and that's how they will show up in the Sociocs inbox.

    ![image](https://user-images.githubusercontent.com/12301512/210254398-7995321f-5e69-42e1-aca1-51c0fe863e5e.png)

You are all set to accept form submissions from your WordPress website!
