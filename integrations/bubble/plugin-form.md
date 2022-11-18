---
label: Sociocs - Form
title: "Bubble plugin :: Sociocs - Form"
order: -100
---

## Introduction

Form plugin (e.g. Contact Us, Appointment Request, Pricing Inquiry form etc.) for Bubble.

When the end user submits the form, it is received in the Sociocs Inbox, form where, you can reply back.

[!button variant="info" target="blank" text="Demo"](https://sociocs-plugins.bubbleapps.io/version-test/form_demo) [!button variant="info" target="blank" text="Plugin page on Bubble"](https://bubble.io/plugin/sociocs---form-1649951381780x698622226169069600)

## Plugin Installation

1. In the Bubble dashboard, go to "*Plugins*".

1. Click on "*+ Add Plugins*".

1. Search for "*Sociocs - Form*".

1. Click on "*Install*".

## Plugin Configuration

### Sociocs

1. Sign up or log in on <a href="https://app.sociocs.com" target="_blank">app.sociocs.com</a>.

1. Select "*Form*" in the "*Connect a new channel*" page. If you are an existing user, after logging in, click on "*Channels*" menu on the top, click on "*+*" button to go to the "*Connect a new channel*" page.

1. Enter "*Form name*", check "*Key authorization*", and click "*Next*". **You don't need to add fill out any other information.** (Even if you would like to add "*reCAPTCHA*" validation in your form, leave "*reCAPTCHA v2*" unchecked in Sociocs. You would have to use Bubble's reCAPTCHA plugin. Instructions are below. For now, you can continue with these steps.)
    ![image](https://user-images.githubusercontent.com/12301512/163722991-2b6a2b66-c343-4cd9-9dd4-eaf04b5208e5.png)

1. On the next page, click "*Done*", which should take you to the Channels page.

1. Click on the "*Form*" channel you just added, and find API URL, and SECRET KEY (value shown under "*Key authorization*").
    ![image](https://user-images.githubusercontent.com/12301512/179737081-2416c1e8-c2bf-4f00-b046-5b5cfdb24e15.png)

### Bubble Editor

1. Go to the "*Sociocs - Form*" plugin in the Bubble Editor.

1. Add "*API URL*" and "*SECRET KEY*" configuration parameters.

1. Bubble also shows fields for adding dev keys (i.e. "*API URL - dev.*", "*SECRET KEY - dev.*"). You can leave them blank.

## Create a form in Bubble Editor

Once the plugin is ready, it's time to create a form in your Bubble app (e.g. Contact Us form)

### Design tab/page

1. Add input fields (e.g. Name, Email address, Message etc.), and a button in your bubble app's page (You can create a separate page for this, or add input fields in an existing page such as index.html). You should also add an "*Alert*" element, to show a message to the user upon the form submission.
    ![image](https://user-images.githubusercontent.com/12301512/163725288-9c8cb66b-2973-41c9-b3cf-28fa7e99cf86.png)

1. If you would like to add reCAPTCHA verification, install and configure Bubble's reCAPTCHA plugin by following the instructions available here: <https://manual.bubble.io/core-resources/bubble-made-plugins/recaptcha>. Add "*reCaptcha form*" element above the submit button you added in the previous step.

### Workflow tab/page

1. If you have added Bubble reCAPTCHA element in the form, add an additional condition in the Button Submit handler to ensure reCAPTCHA checkbox is checked.
    ![image](https://user-images.githubusercontent.com/12301512/163722241-90402851-ae63-499e-b4a0-af9bf40621e3.png)

1. Add a new action for the button.
    ![image](https://user-images.githubusercontent.com/12301512/163722333-6674d3f3-4b7d-49ec-90d3-7b654a793e42.png)

1. In the action popup, select "*Plugins -> Submit Sociocs Form*".
    ![image](https://user-images.githubusercontent.com/12301512/163722506-494526cc-766d-4d44-afbb-4b98320e798c.png)

1. In the "*Submit Sociocs Form*" popup, add key/value mapping for each input field you created.

    - Use lowercase naming for the keys.

    - Email address, and Name field related keys must be called "*email*", and "*name*", so that Sociocs can identify those fields as such.

    - "*email*" key is required.

    - "*name*" key is optional but recommended.

    - For a Contact Us form - keys are usually "*name*", "*email*", and "*message*". If you have additional input fields in your Bubble form, you can add mapping for those too. Name keys how you would like to see them on Sociocs inbox upon form submission.
        ![image](https://user-images.githubusercontent.com/12301512/163722613-00bf0a75-4890-4d7f-aecb-1f2ef1d1345f.png)

1. Add a new action (step 2) for the button.

1. In the action popup, select "*Element action -> Show message*".
    ![image](https://user-images.githubusercontent.com/12301512/163723319-3f953b53-d895-4084-9e3b-8f9fbf01df89.png)

1. In the "*Show message*" popup, select alert element in the "*Element*" dropdown, and add a condition to match step1's result to an "*Arbitrary text*" of "*success*".
    ![image](https://user-images.githubusercontent.com/12301512/163723455-f27722be-5b33-440a-b4e2-9749a6cc9f12.png)

You are all set to accept form submissions in your Bubble app!
