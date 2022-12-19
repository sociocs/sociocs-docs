---
title: Add contact
order: -100
---

Add a new contact. When a given phone number already exists, it updates existing contact.

## Method

[!badge POST]

## Path

`/contact/[phone_number]`

## Path parameter

Name | Value | Required? {class="compact"}
--- | ---
phone_number | {{include "api/phone-number-value"}} | Yes

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
list_id | 0 - to add to "All Contacts" or <br/> List ID - to add to a contact list (List ID is the value shown in the address bar when a list is selected on the Contacts page) | Integer | No (defaults to 0)
phone_number_cc | Phone number country dial code (e.g. "1") | String | No
name | Contact person name | String | No

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Description {class="compact"}
--- | ---
status | `success` or `error` | -
errors | Array of object `{ msg: [error detail] }` | Only present when status is `error`
data | Object `{ id: [new contact id]}` | Only present when status is `success`

## Code sample

+++ cURL

```shell
curl --location --request POST 'https://api.sociocs.com/contact/16175551212' \
--header 'apikey: [your api key]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "list_id": 0,
    "phone_number_cc": "1",
    "name": "John Johnson"
}'
```

+++
