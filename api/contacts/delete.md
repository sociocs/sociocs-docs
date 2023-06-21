---
title: Delete contact
order: -500
---

Delete a contact.

## Method

[!badge DELETE]

## Path

`/contacts/[phone_number]`

## Path parameter

Name | Value | Required? {class="compact"}
--- | ---
phone_number | {{include "api/phone-number-value"}} | Yes

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
list_id | 0 - to delete the contact (including from all the contact lists) or <br/> List ID - to delete only from a contact list (List ID is the value shown in the address bar when a list is selected on the Contacts page)  | Integer | No (defaults to 0)

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
status | `success` or `error` | -
errors | Array of object `{ msg: [error detail] }` | Only present when status is `error`

## Code sample

+++ cURL

```shell
curl --location --request DELETE 'https://api.sociocs.com/contact/16175551212' \
--header 'apikey: [your api key]'
--header 'Content-Type: application/json' \
--data-raw '{
    "list_id_": 0
}'
```

+++
