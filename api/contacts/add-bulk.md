---
title: Add contacts bulk
order: -200
---

Add new contacts in bulk. When a given phone number already exists, it updates existing contact.

## Method

[!badge POST]

## Path

`/contact/bulk`

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
list_id | 0 - to add to "All Contacts" or <br/> List ID - to add to a contact list (List ID is the value shown in the address bar when a list is selected on the Contacts page) | Integer | No (defaults to 0)
phone_number_cc | Phone number country dial code (e.g. "1") | String | No
records |  Array of up to 10,000 contacts `{ phone_number: [phone number starting with country code (required)], name: [contact name (optional)] }` | Array | Yes

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Description {class="compact"}
--- | ---
status | `success` or `error` | -
errors | Array of object `{ msg: [error detail] }` | Only present when status is `error`

## Code sample

+++ cURL

```shell
curl --location --request POST 'https://api.sociocs.com/contact/bulk' \
--header 'apikey: [your api key]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "list_id": 0,
    "phone_number_cc": "1",
    "records": [
        {
            "phone_number": "16175551212",
            "name": "John Johnson"
        },
        {
            "phone_number": "16175551111",
            "name": "David Davidson"
        }
    ]
}'
```

+++
