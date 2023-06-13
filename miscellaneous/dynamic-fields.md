---
title: Dynamic fields
order: -100
---

Dynamic fields help personalize the messages by applying values from the matching fields in the data source for each record.

For example, you can use the message text like below.

![Message example](https://github.com/sociocs/docs/assets/12301512/6f3a05fb-c385-44df-8ec9-9c723cda9ac4)

When the above message is sent, *\{\{BUSINESS_NAME\}\}*, *\{\{CUSTOMER_NAME\}\}*, *\{\{appointment_date\}\}*, *\{\{appointment_time\}\}*, and *\{\{location\}\}* get replaced with applicable values for each recipient.

!!!
Dynamic fields used in the message text are case sensitive. For example, *\{\{appointment_date\}\}* is not same as *\{\{Appointment_Date\}\}*.
!!!

## Predefined fields

Below fields are prefilled, and you can always use them in your message text.

- \{\{BUSINESS_NAME\}\} - Your business name.
- \{\{CUSTOMER_NAME\}\} - Name of the recipient.
- \{\{PHONE_NUMBER\}\} - Phone number of the recipient starting with the country dial code (e.g., 16317471111).
- \{\{SENDER_NAME\}\} - Name of the person sending the bulk messages.

## Fields from your data source

You can use column headers from your CSV/Excel or extra fields from your contact as dynamic field.

### CSV/Excel

When sending bulk messages using a CSV or an Excel file, you can use the column header as the dynamic field within the message text.

For example, if you have a CSV or Excel like below,

![CSV or Excel example](https://github.com/sociocs/docs/assets/12301512/6da7662f-f82d-4c50-8ffb-677bcc507d1a)

You can use ***FirstName*** column header from the file as a dynamic field like this `Hello {%{{{FirstName}}}%}. Nice to see you today...`

### Contact list

When sending bulk messages using a contact list, you can use the extra field as the dynamic field within the message text.

For example, if you have a contact list like below,

![Contact list example](https://github.com/sociocs/docs/assets/12301512/ba6ef733-c1a0-4227-aad2-e34f4c8c29ca)

You can use ***email_address*** extra field as a dynamic field like this `Hello {%{{{CUSTOMER_NAME}}}%}. We tried to get in touch with you on this email address {%{{{email_address}}}%} ...`

## Advanced handling

You can do more with the dynamic fields than just replacing the values from your data source. We have created a few helper functions so that you get more out of the dynamic fields.

### Date formatting

Helps convert the date into a different format of your choice.

- Function name: `dateFormat`
- Usage: `{%{{{#dateFormat "format string"}}}%}{%{{{your dynamic date field}}}%}{%{{{/dateFormat}}}%}`

#### Example

"*appointment_date*" value in your data source might be "*2023-06-15*", but you would like to send it in the message as "*Thursday, June 31, 2023*". You can do so by using *dateFormat* like this `{%{{{#dateFormat "dddd, mmmm d, yyyy"}}}%}{%{{{appointment_date}}}%}{%{{{/dateFormat}}}%}`

#### Format string options

 **Value** | **Description** { class="compact" }
---|---
 d | Day of the month as digits; no leading zero for single-digit days.
 dd | Day of the month as digits; leading zero for single-digit days.
 ddd | Day of the week as a three-letter abbreviation.
 DDD | "Ysd" (for Yesterday), "Tdy" (for Today) or "Tmw" (for Tomorrow), if date lies within these three days. Else fall back to ddd.
 dddd | Day of the week as its full name.
 DDDD | "Yesterday", "Today" or "Tomorrow" if date lies within these three days. Else fall back to dddd.
 m | Month as digits; no leading zero for single-digit months.
 mm | Month as digits; leading zero for single-digit months.
 mmm | Month as a three-letter abbreviation.
 mmmm | Month as its full name.
 yy | Year as last two digits; leading zero for years less than 10.
 yyyy | Year represented by four digits.
 h | Hours; no leading zero for single-digit hours (12-hour clock).
 hh | Hours; leading zero for single-digit hours (12-hour clock).
 H | Hours; no leading zero for single-digit hours (24-hour clock).
 HH | Hours; leading zero for single-digit hours (24-hour clock).
 M | Minutes; no leading zero for single-digit minutes.
 MM | Minutes; leading zero for single-digit minutes.
 N | ISO 8601 numeric representation of the day of the week.
 o | GMT/UTC timezone offset, e.g. -0500 or +0230.
 p | GMT/UTC timezone offset, e.g. -05:00 or +02:30.
 s | Seconds; no leading zero for single-digit seconds.
 ss | Seconds; leading zero for single-digit seconds.
 S | The date's ordinal suffix (st, nd, rd, or th). Works well with d.
 l | Milliseconds; gives 3 digits.
 L | Milliseconds; gives 2 digits.
 t | Lowercase, single-character time marker string: a or p.
 tt | Lowercase, two-character time marker string: am or pm.
 T | Uppercase, single-character time marker string: A or P.
 TT | Uppercase, two-character time marker string: AM or PM.
 W | ISO 8601 week number of the year, e.g. 4, 42
 WW | ISO 8601 week number of the year, leading zero for single-digit, e.g. 04, 42
 Z | US timezone abbreviation, e.g. EST or MDT. For non-US timezones, the GMT/UTC offset is returned, e.g. GMT-0500
