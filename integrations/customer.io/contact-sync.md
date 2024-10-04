---
label: Contact Sync
title: "Sync Customer.io contacts with Sociocs"
order: -400
---

## Introduction

Sync Customer.io people/contacts with Sociocs using a Customer.io campaign.

!!!
The contact syncing works only one way from Customer.io to Sociocs.
!!!

!!!
You need a FREE TRIAL or PAID account on Sociocs to use the necessary API for this integration.
!!!

## Setup on Sociocs

{{include "signup-or-login"}}

1. Go to "*Profile & settings -> API*".
    ![settings](https://user-images.githubusercontent.com/12301512/163997321-90b286f5-e1aa-4df8-bc18-e453b20d26e8.png)

    ![api](https://github.com/sociocs/docs/assets/12301512/4168b133-c8e2-4834-9b7b-d62b5203349c)

1. Find the "*API key*". You'll need it later. If you're using Sociocs API for the first time, you need to enable it by clicking on the "*Enable API*" button.

## Setup on Customer.io

1. Create a new campaign, and go to the "*Trigger*" step. Select any trigger when you might want to send the Customer.io contact to Sociocs.

1. Finish "*Settings*" and "*Goal & Exit*" steps. Go to the "*Workflow*" step. Most likely you don't need to make any changes in the "*Settings*" step, and select "*No goal*" in the "*Goal & Exit*" step.

1. Under the "*Request tab*", select a sample contact with a phone number in the left hand side column.
    !!!
    Phone numbers for your contacts must begin with the country dial code to correctly link them to conversations in the Sociocs inbox (e.g., +16317471111).
    !!!

1. In the right hand side column,

    - Select "*POST*" in the dropdown list.

    - Enter `https://api.sociocs.com/contacts/{%{{{customer.phone}}}%}` in the URL field.

    - Click on "*Add header*". Add `apikey` in the "*NAME*" field, and your api key in the "*VALUE*" field.

    - In the API data payload box shown below, add below JSON object.

    ```
    {
        "list_id": 0,
        "name": "{%{{{ customer.full_name | default: '' }}}%}",
        "extra_fields": {
            "email": "{%{{{ customer.email | default: '' }}}%}"
        }
    }
    ```
    Here's a sample of the API request parameters.
    ![sample api params](https://github.com/user-attachments/assets/91ede00d-4d13-4dad-bdb1-2aebef898861)

    !!!
    If you would like to save your contacts in a contat list in Sociocs, you can add the "*list_id*" value from the Sociocs contacts page.
    !!!

    !!!
    You can send any attribute from the Customer.io contact to save with the Sociocs contact. Add any field under the "*extra_fields*" object like how the "*email*" field is shown above.
    !!!

    !!!
    Notice how every string field and value is wrapped in double quotes, including attributes from the Customer.io contact. You can use any attribute from your contact by clicking the ‘+’ button in your sample contact; however, you need to manually wrap the variable placement with double quotes.
    
    If you would like to use empty as the default value, make sure it's represented only with two quotes (two single quotes for better readability). When adding the field using the Customer.io UI, be aware that it wraps the quotes with an additional set, which should be corrected.
    !!!

1. Click on the "*Send test...*" button to verify that the Customer.io contact shows up in Sociocs.

1. Complete the "*Review*" step and start the campaign.

*Congratulations, you've enabled contact syncing from Customer.io to Sociocs!*

