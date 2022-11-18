---
label: Sociocs - Form
title: "Webflow :: Sociocs - Form"
order: -100
---

## Introduction

Form integration (e.g. Contact Us, Appointment Request, Pricing Inquiry form etc.) for Webflow websites.

When the end user submits the form, it is received in the Sociocs Inbox, form where, you can reply back.

## Form submission options

1. **Direct posting to Sociocs**: With this option, Webflow form is submitted directly to Sociocs form handler. [!button variant="info" target="blank" text="Demo"](https://sociocs-form-demo.webflow.io/)
    - This option allows multiple forms on Webflow submitting to different channels on Sociocs.
    - It is a better choice when you have multiple forms on your website.
    - In the Sociocs Inbox, you can see form name in each conversation to easily identify the type of the form.
    - One downside with this approach is that the user gets redirected from Webflow website to Sociocs form handler page, and gets redirected back to Webflow page after the form data is received. *FYI - unless there is any error, the user won't see the Sociocs page*.

1. **Webhook based submission**: With this option, Webflow handles the form submission, and calls Sociocs webhook from their server to submit form data to Sociocs channel. [!button variant="info" target="blank" text="Demo"](https://sociocs-form-demo-2.webflow.io/)
    - Webflow allows only one webhook for the forms, and hence all the conversations in the Sociocs Inbox have the same form name attached to them.
    - It is a better choice when you have only one form on your website.
    - Form submission takes place using AJAX without user getting redirected.
    - If avoiding user redirects is a must have, one workaround for multiple forms is to add additional hidden field (e.g. "form_type") in each form to identify form type in the Sociocs Inbox. Still, it's not as convenient as seeing specific form name attached to the conversations.

## Setup for Option 1 - Direct submission to Sociocs

### Sociocs

1. Sign up or log in on <a href="https://app.sociocs.com" target="_blank">app.sociocs.com</a>.

1. Select "*Form*" in the "*Connect a new channel*" page. If you are an existing user, after logging in, click on "*Channels*" menu on the top, click on "*+*" button to go to the "*Connect a new channel*" page.

1. Enter "*Form name*", check "*Restrict to domain*", enter your website domain (e.g. sociocs-form-demo.webflow.io).
![image](https://user-images.githubusercontent.com/12301512/202721606-37bb57fe-5f4a-4bb8-b840-9cdd011c49ac.png)

1. If you are planning to add reCAPTCHA to your Webflow form, check "*reCAPTCHA v2*", enter your reCAPTCHA secret key.
![image](https://user-images.githubusercontent.com/12301512/202721739-297755c4-cd44-452a-91f6-b73c574c1776.png)

1. In the "*Redirect URL*", enter URL of the page where the user should be redirected after the form submission (e.g. thank you page), If you don't add a URL, user will be shown a thank you page on Sociocs form page, with a button to go back to your site. *This step is optional.*

1. Enter "*Website URL*", which gets added to the conversation emails sent to the user. *This step is optional.*
![image](https://user-images.githubusercontent.com/12301512/202721761-bc6ce0e8-1ad6-4c32-ad4f-a47f199fb0d0.png)

1. Click "*Next*". On the next page, click "*Done*", which should take you to the Channels page.

1. Click on the "*Form*" channel you just added, and find form's endpoint URL.
![image](https://user-images.githubusercontent.com/12301512/202722000-3e197f36-097a-41f3-a84d-f23a1155ddda.png)

### Webflow

#### Create a form in the Designer

1. Add a "*Form Block*" on your page.
![image](https://user-images.githubusercontent.com/12301512/202722113-35368347-f3ff-4878-a481-13a5b6f1f4ae.png)

1. By default Webflow adds "*Name*" and "*Email address*" fields in the form. **Email address is required for the form to work correctly in Sociocs.**

1. In the field settings, go to "*Element Settings*". In "*Text Fields Settings -> Name*", change value for the "*Name*" to "name" and for the "*Email Address*" field to "email" in lowercase. **These field names MUST be exactly as mentioned and in lowercase.**
![image](https://user-images.githubusercontent.com/12301512/202722401-5406007d-2296-48ba-a6d5-d02c2b6b607f.png)

1. Add additional fields you would like to capture (e.g. "*Message*"). Unlike "*Name*", and "*Email Address*" fields, you can name these additional fields whatever you like.

1. If you enabled "*reCAPTCHA v2*" in the Sociocs Form channel, add the reCAPTCHA element to the form.

1. Select any field or form block on your form, and go to "*Element Settings*" again. In "*Form Settings -> Action*", enter form's endpoint URL from Sociocs. Select "*Method*" as "*POST*".
![image](https://user-images.githubusercontent.com/12301512/202722857-2122e68c-5e64-406e-8413-4cb89c823097.png)

1. You are all set to accept form submissions in your Webflow site!

## Setup for Option 2 - Webhook based submission

### Sociocs

1. Sign up or log in on <a href="https://app.sociocs.com" target="_blank">app.sociocs.com</a>.

1. Select "*Form*" in the "*Connect a new channel*" page. If you are an existing user, after logging in, click on "*Channels*" menu on the top, click on "*+*" button to go to the "*Connect a new channel*" page.

1. Enter "*Form name*", check "*Restrict to domain*", enter your website domain (e.g. sociocs-form-demo.webflow.io).

1. You don't need to check "*reCAPTCHA v2*" here, even if you are planning to add it to your Webflow form. reCAPTCHA validation is handled by Webflow in this case.

1. Enter "*Website URL*", which gets added to the conversation emails sent to the user. *This step is optional.*

1. Click "*Next*". On the next page, click "*Done*", which should take you to the Channels page.

1. Click on the "*Form*" channel you just added, and find form's API URL, and secret key (value shown under "*Key authorization*").

### Webflow

#### Create a form in the Designer

1. Add a "*Form Block*" on your page.
![image](https://user-images.githubusercontent.com/12301512/202722113-35368347-f3ff-4878-a481-13a5b6f1f4ae.png)

1. By default Webflow adds "*Name*" and "*Email address*" fields in the form. **Email address is required for the form to work correctly in Sociocs.**

1. In the field settings, go to "*Element Settings*". In "*Text Fields Settings -> Name*", change value for the "*Name*" to "name" and for the "*Email Address*" field to "email" in lowercase. **These field names MUST be exactly as mentioned and in lowercase.**
![image](https://user-images.githubusercontent.com/12301512/202722401-5406007d-2296-48ba-a6d5-d02c2b6b607f.png)

1. Add additional fields you would like to capture (e.g. "*Message*"). Unlike "*Name*", and "*Email Address*" fields, you can name these additional fields whatever you like.

1. Select any field or form block on your form, and go to "*Element Settings*" again. Make sure "*Form Settings -> Action*" value is blank.

#### Add webhook in Project Settings

1. Go to "*Project Settings*", and go to "*Integrations*" tab.
![image](https://user-images.githubusercontent.com/12301512/202723776-26a92bd4-d635-4eec-bd16-cc11246ed8fa.png)

1. Scroll down to "*Webhooks*" section, and click on "*+ Add Webhook*".
![image](https://user-images.githubusercontent.com/12301512/202723863-94ad6f07-e35a-4b32-8679-049551e582f6.png)

1. Under "*Trigger Type*", select "Form submission". Under "*Webhook URL*", enter form's API URL from Sociocs with "*apikey*" as query string.
    - Here is the format of how the URL should be entered - `[your form's API URL]?apikey=[your secret key]`.
    - Example URL (**DO NOT USE THIS IT IN YOUR FORM**): `https://forms.sociocs.com/v1/ABXLpcxfV78tngkZq6bbq3/1238703332685678?apikey=ABCDTeuZJMTkAbkWs8O456KAa09CsXYZ`.
![image](https://user-images.githubusercontent.com/12301512/202724033-9607053b-dca3-4ce5-8843-58fd529576f2.png)

1. Click "*Add Webhook*". You are all set to accept form submissions in your Webflow site!
