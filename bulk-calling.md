---
title: "Bulk calling"
icon: "https://static.sociocs.com/icons-docs/bulk-calling.svg"
order: -212
---

{{include "alert-paid-account-required"}}

## Introduction

With bulk calling, as the name suggests, you can make numerous voice calls at once to your target audience.

## Channels supporting bulk calling

- SMS (with Twilio)

## Prerequisite

Your account needs to have at least one "*SMS (with Twilio)*" channel.

## Data sources supported

- CSV file
- Excel file
- Contact list

## Message content types supported

- Audio file (aiff, mp3 or wav file of size up to 100mb) [!badge text="Best practices for audio recording" target="_blank"](https://support.twilio.com/hc/en-us/articles/223180588-Best-Practices-for-Audio-Recordings)

## Executing bulk calls

- Go to "*Bulk calling*" from the left sidebar.

- Select a channel from the list of eligible channels in your account.

---

**Provide information for the below fields.**

### Name

Provide a name to easily identify the bulk job/campaign later. For your internal use.

### Audio file

Upload a pre-recorded audio file which will be played when the user picks up the phone or the call goes to the voicemail. To see the list of allowed file types, go to [!badge text="Message content types supported"](#message-content-types-supported).

### Data source

+++ Upload CSV/Excel

![Upload CSV/Excel tab](https://github.com/sociocs/docs/assets/12301512/ace4720a-a57f-4a39-836b-a2aeb0489ccd)

#### File

You can upload a CSV or an Excel file with any number of columns in any order.

This gives you flexibility to directly upload a file exported from another system without a need of any data manipulation. Necessary data mapping are captured in the fields below.

##### Duplicates allowed

Check this box if you would like to call the same number multiple times if duplicates found in the file. Please note that subsequent calls do no wait for the previous call to finish. When unchecked, message is sent only once per phone number. *We recommend to keep this option unchecked unless you have a specific reason not to.*

##### The file's first record doesn't have column headers

When the file you're uploading doesn't have any column headers, you can specify the column headers in text box that shows up once you check this box.

!!! info
This is very helpful when you're exporting the file from another system which doesn't export with column headers. You can specify the column headers here instead of adding to the exported file each time.
!!!

Column headers must be provided separated by comma in the exact order as the file records. For example, if you upload a file like below, you could enter values in the text box like this - `id,full_name,first_name,last_name,phone_number,email_address,date_of_birth,address`.

![File example without column headers](https://github.com/sociocs/docs/assets/12301512/6ceaa641-9048-40ed-9ca6-68477a6d35be)

#### To country code

If the phone numbers in the file do not start with the country dial code (e.g., +1 or 1), you should select the appropriate country dial code in this dropdown list.

!!! info
If the value shown by default is correct, there is no need to change it.
!!!

##### Phone numbers in the uploaded file start with the country code

This option must be checked when the phone numbers in the file you're uploading already start with the country dial code (e.g., +1 or 1).

!!!warning
If the phone numbers in the file already have country dial code, and you don't check this box, the calls may not get delivered because we will apply country code from the "*To country code*" dropdown list.

On the flip side, if the phone numbers in the file do not have country code, and you check this box, the calls may not get delivered at all because they cannot be routed to correct destination number, or they may get delivered incorrectly to recipients in the same country as the source phone number.
!!!

#### Recipient name column header (optional)

!!! info
This field is used only for displaying name when looking at the call list on the "History" page.
!!!

Specify the column header of the recipient name column in the uploaded file.

For example, if you upload a file like below, the value entered should be `Full_Name`.
![File example](https://github.com/sociocs/docs/assets/12301512/4935ce0f-a842-46c9-b79d-bc92be929aa3)

If the file doesn't have column headers, and you checked "*The file's first record doesn't have column headers*", provide the value you entered as the column header for the recipient name column.

#### Phone number column header

Specify the column header of the phone number column in the uploaded file.

For example, if you upload a file like below, the value entered should be `Phone_Number`.
![File example](https://github.com/sociocs/docs/assets/12301512/fb7a8197-a3d3-42bc-9336-7fc42090072b)

If the file doesn't have column headers, and you checked "*The file's first record doesn't have column headers*", provide the value you entered as the column header for the phone number column.

+++ Use Contact List

![Use Contact List tab](https://github.com/sociocs/docs/assets/12301512/246667ba-a663-4dee-a87c-13ef00183f00)

#### Select a list

Select one of the contact lists you have already created. See Contacts for more information.

+++

### Execute on

You can execute calls immediately or schedule it for a later date and time.

!!! info
You can schedule the campaign up to 30 days in advance.
!!!

---

Once you click "*Next*", you will be shown a confirmation popup. You will also be able to make a test call to yourself before confirming the campaign.

In case you need to make any changes, click "*Cancel*" in the confirmation popup to close it.
