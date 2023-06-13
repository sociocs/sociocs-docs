---
title: Add contacts
order: -300
---

There are multiple ways to add contacts to a [!badge text="contact list"](/contacts/contact-lists.md).

## Add a single contact

{{include "go-to-contacts"}}

- Click on a contact list.

- Click on "*Add contact*" button on the top right.

- Enter below information in the popup.
  - Name - Name of the contact person. This field is optional but recommended.
  - Country code - Country dial code for the phone number.
  - Phone number
  - Extra fields - You can add custom fields for the contact here (e.g. email_address). These can be used as dynamic fields in the bulk messaging, or as parameters in the Zapier integration.

## Add multiple contacts

You can upload multiple contacts using a CSV or an Excel file.

{{include "go-to-contacts"}}

- Click on a contact list.

- Click on "*Import contacts*" button on the top right.

---

**Provide below information in the popup.**

![Import contacts popup](https://github.com/sociocs/docs/assets/12301512/87520714-533d-4b24-b0ef-8a271a4e56c2)

### List

Select a contact list you might have created or you can leave it as "*All contacts*". You can also create a new list.

### File

You can upload a CSV or an Excel file with any number of columns in any order. This gives you flexibility to directly upload a file exported from another system without a need of any data manipulation. Necessary data mapping are captured in the fields below.

#### The file's first record doesn't have column headers

When the file you're uploading doesn't have any column headers, you can specify the column headers in text box that shows up once you check this box.

This is very helpful when you're exporting the file from another system which doesn't export with column headers. You can specify the column headers here instead of adding to the exported file.

Column headers must be provided separated by comma in the exact order as the file records. For example, if you upload a file like below, you could enter values in the text box like this - `id,full_name,first_name,last_name,phone_number,email_address,date_of_birth,address`.

![File example without column headers](https://github.com/sociocs/docs/assets/12301512/6ceaa641-9048-40ed-9ca6-68477a6d35be)

### Country code

If the phone numbers in the file do not start with the country dial code (e.g., +1 or 1), you should select the appropriate country dial code in this dropdown list.

#### Phone numbers in the uploaded file start with the country code

This option must be checked when the phone numbers in the file you're uploading already start with the country dial code (e.g., +1 or 1).

### Name column header

Specify the column header of the contact person name column in the uploaded file.

For example, if you upload a file like below, the value entered should be `Full_Name`.
![File example](https://github.com/sociocs/docs/assets/12301512/4935ce0f-a842-46c9-b79d-bc92be929aa3)

If the file doesn't have column headers, and you checked "*The file's first record doesn't have column headers*", provide the value you entered as the column header for the contact person name column.

### Phone number column header

Specify the column header of the phone number column in the uploaded file.

For example, if you upload a file like below, the value entered should be `Phone_Number`.
![File example](https://github.com/sociocs/docs/assets/12301512/fb7a8197-a3d3-42bc-9336-7fc42090072b)

If the file doesn't have column headers, and you checked "*The file's first record doesn't have column headers*", provide the value you entered as the column header for the phone number column.

---

- Once you click "*Next*", you will be shown a confirmation popup with sample records.
- Click "*Confirm*" to upload the contacts.
- In case you need to make any changes, click "*Back*" button, and make necessary changes.

## Add contacts using API

See API documentation [!badge text="Add contact"](/api/contacts/add.md) and [!badge text="Add contacts bulk"](/api/contacts/add-bulk.md).
