---
title: "Bulk messaging"
icon: 'https://static.sociocs.com/icons/bulk-messaging.svg'
order: -200
---

## Introduction

With bulk messaging, as the name suggests, you can send bulk messages to your target audience.

## Channels supporting bulk messaging

- SMS (with Twilio)
- WhatsApp (with Gupshup) (*Future plan, not available at the moment.*)
- WhatsApp (with Twilio) (*Future plan, not available at the moment.*)

## Prerequisite

Your account needs to have at least one "*SMS (with Twilio)*" channel.

## Data sources supported

- CSV file
- Excel file
- Contact list

## Message content types supported

- Text
- Image (gif, jpg, or png)
- Video (mp4 or 3gp)

## Sending bulk messages

- Go to "*Bulk messaging*" from left sidebar.

- Select a channel from the list of eligible channels in your account.

- Provide information for the below fields.

### Message text

Enter message content in this field. You can personalize the messages by adding [!badge text="dynamic fields" target="_blank"](/miscellaneous/dynamic-fields.md) from your data source.

![Message example](https://github.com/sociocs/docs/assets/12301512/7681d3cd-8b50-43be-b970-1a6ef57d7ac5)

### Save as template

You can use this check box to save the entered messages text as a template. It can update an existing template with new text or create a new template.

### Attach media file

In additional to the text, you can also send an image or video in the message.

### Data source

+++ Upload CSV/Excel

#### File

You can upload a CSV or an Excel file with any number of columns in any order. This gives you flexibility to directly upload exported file from any other system without a need of any data manipulation. Necessary data mapping to send the message are captured in the fields below.

##### Duplicates allowed

Check this box if you would like to send multiple messages to the same number if duplicates found in the file. When unchecked, message is sent only once per phone number.

##### The file's first record doesn't have column headers

When the file you're uploading doesn't have any column headers, you can specify the column headers in text box that shows up once you check this box.

This is very helpful when you're exporting the file from another system which doesn't export with column headers. You can specify the column headers here instead of adding to the exported file each time.

Column headers must be provided separated by comma in the exact order as the file records. For example, `customer_name,phone_number,appointment_date,appointment_time`

#### To country code

If the phone numbers in the file do not start with the country dial code (e.g., +1 or 1), you should select the appropriate country dial code in this dropdown list. If the value shown by default is correct, there is no need to change it.

##### Phone numbers in the uploaded file start with the country code

This option must be checked when the phone numbers in the file you're uploading already start with the country dial code (e.g., +1 or 1).

If the phone numbers in the file already have country dial code, and you don't check this box, the messages may not get delivered because we will apply country code from the "*To country code*" dropdown list.

On the flip side, if the phone numbers in the file do not have country code, and you check this box, the messages may not get delivered at all because they cannot be routed to correct destination number or they may get delivered to incorrect recipients in the same country as the source phone number.

#### Recipient name column header

Specify the column header of the recipient name column in the uploaded file.

If the file doesn't have column headers, and you checked "*The file's first record doesn't have column headers*", provide the value you entered as the column header for the recipient name column.

#### Phone number column header

Specify the column header of the phone number column in the uploaded file.

If the file doesn't have column headers, and you checked "*The file's first record doesn't have column headers*", provide the value you entered as the column header for the phone number column.

+++ Use Contact List

#### Select a list

Select one of the contact lists you have already created. See Contacts for more information.

+++

### Send on

You can send the messages immediately or schedule it for a later date and time. You can schedule the campaign up to 30 days in advance.

-----

Once you click *Next*, you will be shown a confirmation popup with a sample preview of the messages that will be sent out. You will also be able to send a test messages to yourself before confirming the campaign.

In case you need to make any changes, you can click cancel in the confirmation popup to close it and make necessary changes.
