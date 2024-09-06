---
title: Send message
order: -200
data:
    path: "/message"
---

- Send a message on Twilio SMS, Twilio WhatsApp or Gupshup WhatsApp channel.
- You can also send an image, a video or a file.
- You can schedule the message to be sent at a future date and time.
- Optionally, you can also save the recipient in a contact list.
- Calling this API with a future schedule date will create a scheduled message, which you can also see and update on app.sociocs.com -> Outbound -> Scheduled.

## Method

[!badge POST]

## Path

`{{path}}`

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
provider | `twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp) | String | Yes
channel_key | Channel key value from *Profile & settings -> API* | String | Yes
to | {{include "api/phone-number-value"}} | String | Yes
name | Recipient name | String | No
text | Message text | String | No (when image_url, image_urls or file_url or template is present)
image_url | Publicly accessible image URL | String | No (when text, video_url or file_url or template is present)
video_url | Publicly accessible video URL | String | No (when text, image_url or file_url or template is present)
file_url | Publicly accessible file URL | String | No (when text, image_url or video_url or template is present)
template | Object with template ID and variables. Used only when provider is either `twlowa` or `gswa`. See below for object format for each provider. | Object | No (when text, image_url or video_url or file_url is present)
contact_saving | Object with instruction to save phone number and name as a contact after sending the message. See below | Object | No
schedule | ISO 8601 date & time (e.g., "2006-01-02T15:04:05-04:00") | String | No

### template

This field is used for passing template details when sending a WhatsApp template message. Applicable only when provider is either `twlowa` or `gswa`.

#### template for provider `twlowa`

Name | Value | Data type | Required? {class="compact"}
--- | ---
id | Template SID from Twilio Content Template Builder | String | Yes
variables | Key value pair object with all the variables in the template. <br/><br/>Example: <br/>`{ "1": "John", "2": "john@example.com", "3": "11-Jul-2024" }` | Object | Yes (only when there are variables in the template)

#### template for provider `gswa`

Name | Value | Data type | Required? {class="compact"}
--- | ---
id | Template ID for the template created in the Gupshup console | String | Yes
variables | Object with `MEDIA_URL` and/or key value pair object maps for each component (`Header`, `Body`, `Buttons`) with variables in the template. <br/><br/>Example: <br/>`{ "MEDIA_URL": "https://placehold.co/600x400", "Header": { "1": "John"}, "Body": { "1": "john@example.com", "2": "11-Jul-2024"}, "Buttons": {"1": "Quick Reply Text"} }` | Object | Yes (only when there are variables in the template)

### contact_saving

This field is for passing instruction to save phone number and name as a contact. If the contact already exists, it will be updated. Extra custom fields can also be passed.

Name | Value | Data type | Required? {class="compact"}
--- | ---
save | `true` - Save phone number, name and extra fields as a contact, <br /> `false` - Skip saving as contact | Boolean | No (defaults to `false`)
list_id | {{include "api/contact-list-id-value"}} | Integer | No (defaults to `0`)
extra_fields | {{include "api/contact-extra-fields-value"}} | Object | No

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Object `{ message_id: [new message id] }` | Only present when status is `success`.

## Code samples

### Sending only text content

+++ cURL

```shell
curl --location --request POST '{{apiBaseUrl}}{{path_for_sample ?? path}}' \
{{include "curl/header-apikey"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "provider": "twlo",
    "channel_key": "your_channel_key",
    "to": "phone_number",
    "name": "recipient_name",
    "text": "message"
}'
```

+++ cURL (Windows)

```shell
curl --location "{{apiBaseUrl}}{{path_for_sample ?? path}}" --header "Content-Type: application/json" --header "apikey: your_api_key" --data "{ \"provider\": \"twlo\", \"channel_key\": \"your_channel_key\", \"to\": \"phone_number\", \"name\": \"recipient_name\", \"text\": \"message\" }"
```

+++ C#

```c#
var client = new HttpClient();
var request = new HttpRequestMessage(HttpMethod.Post, "{{apiBaseUrl}}{{path_for_sample ?? path}}");
request.Headers.Add("apikey", "your_api_key");
var content = new StringContent("{ \"provider\": \"twlo\", \"channel_key\": \"your_channel_key\", \"to\": \"phone_number\", \"name\": \"recipient_name\", \"text\": \"message\" }", null, "application/json");
request.Content = content;
var response = await client.SendAsync(request);
response.EnsureSuccessStatusCode();
Console.WriteLine(await response.Content.ReadAsStringAsync());

```

+++ Dart

```dart
var headers = {
  'Content-Type': 'application/json',
  'apikey': 'your_api_key'
};

var request = http.Request('POST', Uri.parse('{{apiBaseUrl}}{{path_for_sample ?? path}}'));

request.body = json.encode({
  "provider": "twlo",
  "channel_key": "your_channel_key",
  "to": "phone_number",
  "name": "recipient_name",
  "text": "message"
});

request.headers.addAll(headers);

http.StreamedResponse response = await request.send();

if (response.statusCode == 200) {
  print(await response.stream.bytesToString());
}
else {
  print(response.reasonPhrase);
}
```

+++ Go

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "{{apiBaseUrl}}{{path_for_sample ?? path}}"
  method := "POST"

  payload := strings.NewReader(`{`+"
"+`
    "provider": "twlo",`+"
"+`
    "channel_key": "your_channel_key",`+"
"+`
    "to": "phone_number",`+"
"+`
    "name": "recipient_name",`+"
"+`
    "text": "message"`+"
"+`
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("Content-Type", "application/json")
  req.Header.Add("apikey", "your_api_key")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

+++ Java

```java
// This sample uses OkHttp library
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"provider\": \"twlo\",\r\n    \"channel_key\": \"your_channel_key\",\r\n    \"to\": \"phone_number\",\r\n    \"name\": \"recipient_name\",\r\n    \"text\": \"message\"\r\n}");
Request request = new Request.Builder()
  .url("{{apiBaseUrl}}{{path_for_sample ?? path}}")
  .method("POST", body)
  .addHeader("Content-Type", "application/json")
  .addHeader("apikey", "your_api_key")
  .build();
Response response = client.newCall(request).execute();
```

+++ Node.js

```javascript
// This sample uses Axios library
const axios = require('axios');
let data = JSON.stringify({
  "provider": "twlo",
  "channel_key": "your_channel_key",
  "to": "phone_number",
  "name": "recipient_name",
  "text": "message"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: '{{apiBaseUrl}}{{path_for_sample ?? path}}',
  headers: { 
    'Content-Type': 'application/json', 
    'apikey': 'your_api_key'
  },
  data : data
};

axios.request(config)
.then((response) => {
  console.log(JSON.stringify(response.data));
})
.catch((error) => {
  console.log(error);
});

```

+++ PHP

```php
<?php
// This sample uses Guzzle library
$client = new Client();
$headers = [
  'Content-Type' => 'application/json',
  'apikey' => 'your_api_key'
];
$body = '{
  "provider": "twlo",
  "channel_key": "your_channel_key",
  "to": "phone_number",
  "name": "recipient_name",
  "text": "message"
}';
$request = new Request('POST', '{{apiBaseUrl}}{{path_for_sample ?? path}}', $headers, $body);
$res = $client->sendAsync($request)->wait();
echo $res->getBody();
```

+++ Python

```python
# This sample uses Requests library
import requests
import json

url = "{{apiBaseUrl}}{{path_for_sample ?? path}}"

payload = json.dumps({
  "provider": "twlo",
  "channel_key": "your_channel_key",
  "to": "phone_number",
  "name": "recipient_name",
  "text": "message"
})
headers = {
  'Content-Type': 'application/json',
  'apikey': 'your_api_key'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

+++

### Sending text & image

+++ cURL

```shell
curl --location --request POST '{{apiBaseUrl}}{{path_for_sample ?? path}}' \
{{include "curl/header-apikey"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "provider": "twlo",
    "channel_key": "your_channel_key",
    "to": "phone_number",
    "name": "recipient_name",
    "text": "message",
    "image_url": "https://fastly.picsum.photos/id/1068/200/300.jpg?hmac=ICIwYXRGTpDxBPZAI7V8YxGtBBanV8Dfbe_DLNKtYcE"
}'
```

+++ cURL (Windows)

```shell
curl --location "{{apiBaseUrl}}{{path_for_sample ?? path}}" --header "Content-Type: application/json" --header "apikey: your_api_key" --data "{ \"provider\": \"twlo\", \"channel_key\": \"your_channel_key\", \"to\": \"phone_number\", \"name\": \"recipient_name\", \"text\": \"message\", \"image_url\": \"https://fastly.picsum.photos/id/1068/200/300.jpg?hmac=ICIwYXRGTpDxBPZAI7V8YxGtBBanV8Dfbe_DLNKtYcE\"}"
```

+++ C#

```c#
var client = new HttpClient();
var request = new HttpRequestMessage(HttpMethod.Post, "{{apiBaseUrl}}{{path_for_sample ?? path}}");
request.Headers.Add("apikey", "your_api_key");
var content = new StringContent("{ \"provider\": \"twlo\", \"channel_key\": \"your_channel_key\", \"to\": \"phone_number\", \"name\": \"recipient_name\", \"text\": \"message\", \"image_url\": \"https://fastly.picsum.photos/id/1068/200/300.jpg?hmac=ICIwYXRGTpDxBPZAI7V8YxGtBBanV8Dfbe_DLNKtYcE\" }", null, "application/json");
request.Content = content;
var response = await client.SendAsync(request);
response.EnsureSuccessStatusCode();
Console.WriteLine(await response.Content.ReadAsStringAsync());

```

+++ Dart

```dart
var headers = {
  'Content-Type': 'application/json',
  'apikey': 'your_api_key'
};

var request = http.Request('POST', Uri.parse('{{apiBaseUrl}}{{path_for_sample ?? path}}'));

request.body = json.encode({
  "provider": "twlo",
  "channel_key": "your_channel_key",
  "to": "phone_number",
  "name": "recipient_name",
  "text": "message",
  "image_url": "https://fastly.picsum.photos/id/1068/200/300.jpg?hmac=ICIwYXRGTpDxBPZAI7V8YxGtBBanV8Dfbe_DLNKtYcE"
});

request.headers.addAll(headers);

http.StreamedResponse response = await request.send();

if (response.statusCode == 200) {
  print(await response.stream.bytesToString());
}
else {
  print(response.reasonPhrase);
}
```

+++ Go

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "{{apiBaseUrl}}{{path_for_sample ?? path}}"
  method := "POST"

  payload := strings.NewReader(`{`+"
"+`
    "provider": "twlo",`+"
"+`
    "channel_key": "your_channel_key",`+"
"+`
    "to": "phone_number",`+"
"+`
    "name": "recipient_name",`+"
"+`
    "text": "message"`+"
"+`
    "image_url": "https://fastly.picsum.photos/id/1068/200/300.jpg?hmac=ICIwYXRGTpDxBPZAI7V8YxGtBBanV8Dfbe_DLNKtYcE"`+"
"+`
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("Content-Type", "application/json")
  req.Header.Add("apikey", "your_api_key")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

+++ Java

```java
// This sample uses OkHttp library
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"provider\": \"twlo\",\r\n    \"channel_key\": \"your_channel_key\",\r\n    \"to\": \"phone_number\",\r\n    \"name\": \"recipient_name\",\r\n    \"text\": \"message\"\r\n}");
Request request = new Request.Builder()
  .url("{{apiBaseUrl}}{{path_for_sample ?? path}}")
  .method("POST", body)
  .addHeader("Content-Type", "application/json")
  .addHeader("apikey", "your_api_key")
  .build();
Response response = client.newCall(request).execute();
```

+++ Node.js

```javascript
// This sample uses Axios library
const axios = require('axios');
let data = JSON.stringify({
  "provider": "twlo",
  "channel_key": "your_channel_key",
  "to": "phone_number",
  "name": "recipient_name",
  "text": "message",
  "image_url": "https://fastly.picsum.photos/id/1068/200/300.jpg?hmac=ICIwYXRGTpDxBPZAI7V8YxGtBBanV8Dfbe_DLNKtYcE"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: '{{apiBaseUrl}}{{path_for_sample ?? path}}',
  headers: { 
    'Content-Type': 'application/json', 
    'apikey': 'your_api_key'
  },
  data : data
};

axios.request(config)
.then((response) => {
  console.log(JSON.stringify(response.data));
})
.catch((error) => {
  console.log(error);
});

```

+++ PHP

```php
<?php
// This sample uses Guzzle library
$client = new Client();
$headers = [
  'Content-Type' => 'application/json',
  'apikey' => 'your_api_key'
];
$body = '{
  "provider": "twlo",
  "channel_key": "your_channel_key",
  "to": "phone_number",
  "name": "recipient_name",
  "text": "message".
  "image_url": "https://fastly.picsum.photos/id/1068/200/300.jpg?hmac=ICIwYXRGTpDxBPZAI7V8YxGtBBanV8Dfbe_DLNKtYcE"
}';
$request = new Request('POST', '{{apiBaseUrl}}{{path_for_sample ?? path}}', $headers, $body);
$res = $client->sendAsync($request)->wait();
echo $res->getBody();
```

+++ Python

```python
# This sample uses Requests library
import requests
import json

url = "{{apiBaseUrl}}{{path_for_sample ?? path}}"

payload = json.dumps({
  "provider": "twlo",
  "channel_key": "your_channel_key",
  "to": "phone_number",
  "name": "recipient_name",
  "text": "message",
  "image_url": "https://fastly.picsum.photos/id/1068/200/300.jpg?hmac=ICIwYXRGTpDxBPZAI7V8YxGtBBanV8Dfbe_DLNKtYcE"
})
headers = {
  'Content-Type': 'application/json',
  'apikey': 'your_api_key'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

+++

### Sending only an image

+++ cURL

```shell
curl --location --request POST '{{apiBaseUrl}}{{path_for_sample ?? path}}' \
{{include "curl/header-apikey"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "provider": "twlo",
    "channel_key": "your_channel_key",
    "to": "phone_number",
    "name": "recipient_name",
    "image_url": "https://fastly.picsum.photos/id/701/200/300.jpg?hmac=gVWdD9Rh_J0iGXpXOJAN7MZpGPrpeHX_M5JwGGvTSsI"
}'
```

+++ cURL (Windows)

```shell
curl --location "{{apiBaseUrl}}{{path_for_sample ?? path}}" --header "Content-Type: application/json" --header "apikey: your_api_key" --data "{ \"provider\": \"twlo\", \"channel_key\": \"your_channel_key\", \"to\": \"phone_number\", \"name\": \"recipient_name\", \"image_url\": \"https://fastly.picsum.photos/id/701/200/300.jpg?hmac=gVWdD9Rh_J0iGXpXOJAN7MZpGPrpeHX_M5JwGGvTSsI\" }"
```

+++ C#

```c#
var client = new HttpClient();
var request = new HttpRequestMessage(HttpMethod.Post, "{{apiBaseUrl}}{{path_for_sample ?? path}}");
request.Headers.Add("apikey", "your_api_key");
var content = new StringContent("{ \"provider\": \"twlo\", \"channel_key\": \"your_channel_key\", \"to\": \"phone_number\", \"name\": \"recipient_name\", \"image_url\": \"https://fastly.picsum.photos/id/701/200/300.jpg?hmac=gVWdD9Rh_J0iGXpXOJAN7MZpGPrpeHX_M5JwGGvTSsI\" }", null, "application/json");
request.Content = content;
var response = await client.SendAsync(request);
response.EnsureSuccessStatusCode();
Console.WriteLine(await response.Content.ReadAsStringAsync());

```

+++ Dart

```dart
var headers = {
  'Content-Type': 'application/json',
  'apikey': 'your_api_key'
};
var request = http.Request('POST', Uri.parse('{{apiBaseUrl}}{{path_for_sample ?? path}}'));
request.body = json.encode({
  "provider": "twlo",
  "channel_key": "your_channel_key",
  "to": "phone_number",
  "name": "recipient_name",
  "image_url": "https://fastly.picsum.photos/id/701/200/300.jpg?hmac=gVWdD9Rh_J0iGXpXOJAN7MZpGPrpeHX_M5JwGGvTSsI",
});
request.headers.addAll(headers);

http.StreamedResponse response = await request.send();

if (response.statusCode == 200) {
  print(await response.stream.bytesToString());
}
else {
  print(response.reasonPhrase);
}
```

+++ Go

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "{{apiBaseUrl}}{{path_for_sample ?? path}}"
  method := "POST"

  payload := strings.NewReader(`{`+"
"+`
    "provider": "twlo",`+"
"+`
    "channel_key": "your_channel_key",`+"
"+`
    "to": "phone_number",`+"
"+`
    "name": "recipient_name",`+"
"+`
    "image_url": "https://fastly.picsum.photos/id/701/200/300.jpg?hmac=gVWdD9Rh_J0iGXpXOJAN7MZpGPrpeHX_M5JwGGvTSsI",`+"
"+`
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("Content-Type", "application/json")
  req.Header.Add("apikey", "your_api_key")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

+++ Java

```java
// This sample uses OkHttp library
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"provider\": \"twlo\",\r\n    \"channel_key\": \"your_channel_key\",\r\n    \"to\": \"phone_number\",\r\n    \"name\": \"recipient_name\",\r\n    \"image_url\": \"https://fastly.picsum.photos/id/701/200/300.jpg?hmac=gVWdD9Rh_J0iGXpXOJAN7MZpGPrpeHX_M5JwGGvTSsI\",\r\n }");
Request request = new Request.Builder()
  .url("{{apiBaseUrl}}{{path_for_sample ?? path}}")
  .method("POST", body)
  .addHeader("Content-Type", "application/json")
  .addHeader("apikey", "your_api_key")
  .build();
Response response = client.newCall(request).execute();
```

+++ Node.js

```javascript
// This sample uses Axios library
const axios = require('axios');
let data = JSON.stringify({
  "provider": "twlo",
  "channel_key": "your_channel_key",
  "to": "phone_number",
  "name": "recipient_name",
  "image_url": "https://fastly.picsum.photos/id/701/200/300.jpg?hmac=gVWdD9Rh_J0iGXpXOJAN7MZpGPrpeHX_M5JwGGvTSsI",
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: '{{apiBaseUrl}}{{path_for_sample ?? path}}',
  headers: { 
    'Content-Type': 'application/json', 
    'apikey': 'your_api_key'
  },
  data : data
};

axios.request(config)
.then((response) => {
  console.log(JSON.stringify(response.data));
})
.catch((error) => {
  console.log(error);
});
```

+++ PHP

```php
<?php
// This sample uses Guzzle library
$client = new Client();
$headers = [
  'Content-Type' => 'application/json',
  'apikey' => 'your_api_key'
];
$body = '{
  "provider": "twlo",
  "channel_key": "your_channel_key",
  "to": "phone_number",
  "name": "recipient_name",
  "image_url": "https://fastly.picsum.photos/id/701/200/300.jpg?hmac=gVWdD9Rh_J0iGXpXOJAN7MZpGPrpeHX_M5JwGGvTSsI"
}';
$request = new Request('POST', '{{apiBaseUrl}}{{path_for_sample ?? path}}', $headers, $body);
$res = $client->sendAsync($request)->wait();
echo $res->getBody();
```

+++ Python

```python
# This sample uses Requests library
import requests
import json

url = "{{apiBaseUrl}}{{path_for_sample ?? path}}"

payload = json.dumps({
  "provider": "twlo",
  "channel_key": "your_channel_key",
  "to": "phone_number",
  "name": "recipient_name",
  "image_url": "https://fastly.picsum.photos/id/701/200/300.jpg?hmac=gVWdD9Rh_J0iGXpXOJAN7MZpGPrpeHX_M5JwGGvTSsI"
})
headers = {
  'Content-Type': 'application/json',
  'apikey': 'your_api_key'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

+++

### Response object examples

#### When the API call was successful

```json
{
    "status": "success",
    "data": { "message_id": "Xyz12345" }
}
```

#### When the API call was unsuccessful

```json
{
    "status": "error",
    "errors": [{ "msg": "Invalid channel_key." }]
}
```
