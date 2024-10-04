---
label: WhatsApp Campaign
title: "WhatsApp Campaign from Customer.io"
order: -300
---

## Introduction

You can send WhatsApp campaigns from Customer.io using Sociocs and manage the conversation in the Sociocs inbox when someone replies.

!!!
You need a FREE TRIAL or PAID account on Sociocs to use the necessary API for this integration.
!!!

!!!
This integration requires an approved WhatsApp template to successfully send the message. You need to get one approved on the website of the provider you will be using (i.e., Twilio or Gupshup).
!!!

## Supported channels

- WhatsApp (with Twilio)
- WhatsApp (with Gupshup)

## Setup on Sociocs

{{include "signup-or-login"}}

1. Connect "*WhatsApp (with Gupshup)*" or "*WhatsApp (with Twilio)*" channel on the "*Connect a new channel*" page. If you're an existing user, after logging in, click on "*Channels*" menu on the top, click on "*+*" button to go to the "*Connect a new channel*" page.

1. Go to "*Profile & settings -> API*".
    ![settings](https://user-images.githubusercontent.com/12301512/163997321-90b286f5-e1aa-4df8-bc18-e453b20d26e8.png)

    ![api](https://github.com/sociocs/docs/assets/12301512/4168b133-c8e2-4834-9b7b-d62b5203349c)

1. Find the "*API key*" and "*Channel Key*". You'll need them later. If you're using Sociocs API for the first time, you need to enable it by clicking on the "*Enable API*" button.

## Setup on Customer.io

1. Create a new campaign, and go to the "*Trigger*" step. Select any trigger applicable for your needs. Here is an example of a segment trigger, which sends SMS when a contact enters the "*twlosms*" segment.

![trigger](https://github.com/user-attachments/assets/5a250df1-0c65-413d-ba12-b5af8b20f141)

!!!
Select "*Every re-match*" or "*On every event*" under the "*Frequency*" if you would like to send SMS each time the condition occurs. :bulb:
!!!

1. Finish "*Settings*" and "*Goal & Exit*" steps. Go to the "*Workflow*" step.

1. Drag and drop "*Send and Receive Data*" action in your workflow.
    ![send and receive data action](https://github.com/user-attachments/assets/ec886715-8e7c-4949-80e9-901ac6524b18)

1. Click on the action you just added, give it a name, and click on "*Add Request*" button. It will take you to the action setup page.
    ![action popup](https://github.com/user-attachments/assets/14ed16ac-830d-4841-8464-4c45801cfab5)

1. Under the "*Request tab*", select a sample contact with a phone number in the left hand side column.
    !!!
    Phone numbers for your contacts must begin with the country dial code for successfull delivery of the messages (e.g., +16317471111).
    !!!

1. In the right hand side column,

    - Select "*POST*" in the dropdown list.

    - Enter `https://api.sociocs.com/message` in the URL field.

    - Click on "*Add header*". Add `apikey` in the "*NAME*" field, and your api key in the "*VALUE*" field.

    - In the API data payload box shown below, add JSON object as described below.

    ### Request parameters for Twilio WhatsApp channel

    ```
    {
        "provider": "twlowa",
        "channel_key": "your whatsapp channel key",
        "to": "{%{{{ customer.phone }}}%}",
        "name": "{%{{{ customer.full_name | default: '' }}}%}",
        "template": {
            "id": "Template SID from Twilio Content Template Builder",
            "variables": {
                "1": "{%{{{ customer.first_name | default: '-' }}}%}"
            }
        },
        "contact_saving": {
            "save": true,
            "extra_fields": {
                "email": "{%{{{ customer.email | default: '' }}}%}"
            }
        }    
    }
    ```

    Here's a sample of the API request parameters.
    ![sample api params](https://github.com/user-attachments/assets/379f9065-fc2b-46b8-aa93-c9c41199af93)

    ### Request parameters for Gupshup WhatsApp channel

    ```
    {
        "provider": "gswa",
        "channel_key": "your whatsapp channel key",
        "to": "{%{{{ customer.phone }}}%}",
        "name": "{%{{{ customer.full_name | default: '' }}}%}",
        "template": {
            "id": "Template ID for the template created in the Gupshup console	",
            "variables": {
                "Body": {
                    "1": "{%{{{ customer.first_name | default: '-' }}}%}"
                }
            }
        },
        "contact_saving": {
            "save": true,
            "extra_fields": {
                "email": "{%{{{ customer.email | default: '' }}}%}"
            }
        }    
    }
    ```

    Here's a sample of the API request parameters.
    ![sample api params](https://github.com/user-attachments/assets/59fde100-765a-4988-b4ef-55c8806033e8)

    !!!
    If you not want to save contact in Sociocs, you can remove the "contact_saving" object from the above. If you choose to do so, please ensure that you remove the comma at the end of the previous line.

    You can send any attribute from the Customer.io contact to save with the Sociocs contact. Add any field under the "*contact_saving → extra_fields*" object like how the "*email*" field is shown above.
    !!!

    !!!
    Notice how every field and value is wrapped in double quotes, including attributes from the Customer.io contact. You can use any attribute from your contact by clicking the ‘+’ button in your sample contact; however, you need to manually wrap the variable placement with double quotes.

    If you would like to use empty as the default value, make sure it's represented only with two quotes (two single quotes for better readability). When adding the field using the Customer.io UI, be aware that it wraps the quotes with an additional set, which should be corrected.
    !!!

    !!!
    All the variables in your WhatsApp template must be added in the request. In case your Customer.io contact doesn't have a value for a specific variable, you should default it with a non-empty string.
    !!!

1. Click on the "*Send test...*" button to verify that the message gets sent to the sample contact.

1. Complete the "*Review*" step and start the campaign.

*That's it, you are all set to send messages to your target recipients!*