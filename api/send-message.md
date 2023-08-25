---
title: Send message
order: -300
---

- Send a message on Twilio SMS, Twilio WhatsApp or Gupshup WhatsApp channel.
- You can also send one or more images or a file.
- Optionally, you can also save recipient in a contact list.

## Method

[!badge POST]

## Path

`/messages`

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
provider | `twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp) | String | Yes
channel_key | Channel key value from *Profile & settings -> API* | String | Yes
to | {{include "api/phone-number-value"}} | String | Yes
name | Recipient name | String | No
text | Message text | String | No (when image_url, image_urls or file_url is present)
image_url | Publicly accessible image URL | String | No (when text, image_urls or file_url is present)
image_urls | Array of publicly accessible image URLs | String | No (when text, image_url or file_url is present)
file_url | Publicly accessible file URL | String | No (when text, image_url or image_urls is present)
contact_saving | Object with instruction to save phone number and name as a contact after sending the message. See below | Object | No

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
status | `success` or `error` | -
errors | Array of object `{ msg: [error detail] }` | Only present when status is `error`

## Code samples

### Sending only text content

+++ cURL

```shell
curl --location --request POST 'https://api.sociocs.com/message' \
--header 'apikey: [your api key]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "provider": "[provider]",
    "channel_key": "[your channel key]",
    "to": "[phone number]",
    "name": "[recipient name]",
    "text": "[message]"
}'
```

+++ cURL (Windows)

```shell
curl --location "https://api.sociocs.com/message" --header "Content-Type: application/json" --header "apikey: [your api key]" --data "{ \"provider\": \"[provider]\", \"channel_key\": \"[your channel key]\", \"to\": \"[phone number]\", \"name\": \"[recipient name]\", \"text\": \"[message]\" }"
```

+++ C#

```c#
var client = new HttpClient();
var request = new HttpRequestMessage(HttpMethod.Post, "https://api.sociocs.com/message");
request.Headers.Add("apikey", "[your api key]");
var content = new StringContent("{ \"provider\": \"[provider]\", \"channel_key\": \"[your channel key]\", \"to\": \"[phone number]\", \"name\": \"[recipient name]\", \"text\": \"[message]\" }", null, "application/json");
request.Content = content;
var response = await client.SendAsync(request);
response.EnsureSuccessStatusCode();
Console.WriteLine(await response.Content.ReadAsStringAsync());

```

+++ Dart

```dart
var headers = {
  'Content-Type': 'application/json',
  'apikey': '[your api key]'
};

var request = http.Request('POST', Uri.parse('https://api.sociocs.com/message'));

request.body = json.encode({
  "provider": "[provider]",
  "channel_key": "[your channel key]",
  "to": "[phone number]",
  "name": "[recipient name]",
  "text": "[message]"
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

  url := "https://api.sociocs.com/message"
  method := "POST"

  payload := strings.NewReader(`{`+"
"+`
    "provider": "[provider]",`+"
"+`
    "channel_key": "[your channel key]",`+"
"+`
    "to": "[phone number]",`+"
"+`
    "name": "[recipient name]",`+"
"+`
    "text": "[message]"`+"
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
  req.Header.Add("apikey", "[your api key]")

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
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"provider\": \"[provider]\",\r\n    \"channel_key\": \"[your channel key]\",\r\n    \"to\": \"[phone number]\",\r\n    \"name\": \"[recipient name]\",\r\n    \"text\": \"[message]\"\r\n}");
Request request = new Request.Builder()
  .url("https://api.sociocs.com/message")
  .method("POST", body)
  .addHeader("Content-Type", "application/json")
  .addHeader("apikey", "[your api key]")
  .build();
Response response = client.newCall(request).execute();
```

+++ Node.js

```javascript
// This sample uses Axios library
const axios = require('axios');
let data = JSON.stringify({
  "provider": "[provider]",
  "channel_key": "[your channel key]",
  "to": "[phone number]",
  "name": "[recipient name]",
  "text": "[message]"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://api.sociocs.com/message',
  headers: { 
    'Content-Type': 'application/json', 
    'apikey': '[your api key]'
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
  'apikey' => '[your api key]'
];
$body = '{
  "provider": "[provider]",
  "channel_key": "[your channel key]",
  "to": "[phone number]",
  "name": "[recipient name]",
  "text": "[message]"
}';
$request = new Request('POST', 'https://api.sociocs.com/message', $headers, $body);
$res = $client->sendAsync($request)->wait();
echo $res->getBody();
```

+++ Python

```python
# This sample uses Requests library
import requests
import json

url = "https://api.sociocs.com/message"

payload = json.dumps({
  "provider": "[provider]",
  "channel_key": "[your channel key]",
  "to": "[phone number]",
  "name": "[recipient name]",
  "text": "[message]"
})
headers = {
  'Content-Type': 'application/json',
  'apikey': '[your api key]'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

+++

### Sending text & image

+++ cURL

```shell
curl --location --request POST 'https://api.sociocs.com/message' \
--header 'apikey: [your api key]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "provider": "[provider]",
    "channel_key": "[your channel key]",
    "to": "[phone number]",
    "name": "[recipient name]",
    "text": "[message]",
    "image_url": "[image url]"
}'
```

+++ cURL (Windows)

```shell
curl --location "https://api.sociocs.com/message" --header "Content-Type: application/json" --header "apikey: [your api key]" --data "{ \"provider\": \"[provider]\", \"channel_key\": \"[your channel key]\", \"to\": \"[phone number]\", \"name\": \"[recipient name]\", \"text\": \"[message]\", \"image_url\": \"[image url]\"}"
```

+++ C#

```c#
var client = new HttpClient();
var request = new HttpRequestMessage(HttpMethod.Post, "https://api.sociocs.com/message");
request.Headers.Add("apikey", "[your api key]");
var content = new StringContent("{ \"provider\": \"[provider]\", \"channel_key\": \"[your channel key]\", \"to\": \"[phone number]\", \"name\": \"[recipient name]\", \"text\": \"[message]\", \"image_url\": \"[image url]\" }", null, "application/json");
request.Content = content;
var response = await client.SendAsync(request);
response.EnsureSuccessStatusCode();
Console.WriteLine(await response.Content.ReadAsStringAsync());

```

+++ Dart

```dart
var headers = {
  'Content-Type': 'application/json',
  'apikey': '[your api key]'
};

var request = http.Request('POST', Uri.parse('https://api.sociocs.com/message'));

request.body = json.encode({
  "provider": "[provider]",
  "channel_key": "[your channel key]",
  "to": "[phone number]",
  "name": "[recipient name]",
  "text": "[message]",
  "image_url": "[image url]"
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

  url := "https://api.sociocs.com/message"
  method := "POST"

  payload := strings.NewReader(`{`+"
"+`
    "provider": "[provider]",`+"
"+`
    "channel_key": "[your channel key]",`+"
"+`
    "to": "[phone number]",`+"
"+`
    "name": "[recipient name]",`+"
"+`
    "text": "[message]"`+"
"+`
    "image_url": "[image url]"`+"
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
  req.Header.Add("apikey", "[your api key]")

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
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"provider\": \"[provider]\",\r\n    \"channel_key\": \"[your channel key]\",\r\n    \"to\": \"[phone number]\",\r\n    \"name\": \"[recipient name]\",\r\n    \"text\": \"[message]\"\r\n}");
Request request = new Request.Builder()
  .url("https://api.sociocs.com/message")
  .method("POST", body)
  .addHeader("Content-Type", "application/json")
  .addHeader("apikey", "[your api key]")
  .build();
Response response = client.newCall(request).execute();
```

+++ Node.js

```javascript
// This sample uses Axios library
const axios = require('axios');
let data = JSON.stringify({
  "provider": "[provider]",
  "channel_key": "[your channel key]",
  "to": "[phone number]",
  "name": "[recipient name]",
  "text": "[message]",
  "image_url": "[image url]"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://api.sociocs.com/message',
  headers: { 
    'Content-Type': 'application/json', 
    'apikey': '[your api key]'
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
  'apikey' => '[your api key]'
];
$body = '{
  "provider": "[provider]",
  "channel_key": "[your channel key]",
  "to": "[phone number]",
  "name": "[recipient name]",
  "text": "[message]".
  "image_url": "[image url]"
}';
$request = new Request('POST', 'https://api.sociocs.com/message', $headers, $body);
$res = $client->sendAsync($request)->wait();
echo $res->getBody();
```

+++ Python

```python
# This sample uses Requests library
import requests
import json

url = "https://api.sociocs.com/message"

payload = json.dumps({
  "provider": "[provider]",
  "channel_key": "[your channel key]",
  "to": "[phone number]",
  "name": "[recipient name]",
  "text": "[message]",
  "image_url": "[image url]"
})
headers = {
  'Content-Type': 'application/json',
  'apikey': '[your api key]'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

+++

### Sending only images

+++ cURL

```shell
curl --location --request POST 'https://api.sociocs.com/message' \
--header 'apikey: [your api key]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "provider": "[provider]",
    "channel_key": "[your channel key]",
    "to": "[phone number]",
    "name": "[recipient name]",
    "image_urls": [
        "[image url 1]",
        "[image url 2]",
        "[image url 3]"
    ]
}'
```

+++ cURL (Windows)

```shell
curl --location "https://api.sociocs.com/message" --header "Content-Type: application/json" --header "apikey: [your api key]" --data "{ \"provider\": \"[provider]\", \"channel_key\": \"[your channel key]\", \"to\": \"[phone number]\", \"name\": \"[recipient name]\", \"image_urls\": [\"[image url 1]\", \"[image url 2]\", \"[image url 3]\"] }"
```

+++ C#

```c#
var client = new HttpClient();
var request = new HttpRequestMessage(HttpMethod.Post, "https://api.sociocs.com/message");
request.Headers.Add("apikey", "[your api key]");
var content = new StringContent("{ \"provider\": \"[provider]\", \"channel_key\": \"[your channel key]\", \"to\": \"[phone number]\", \"name\": \"[recipient name]\", \"image_urls\": [\"[image url 1]\", \"[image url 2]\", \"[image url 3]\"] }", null, "application/json");
request.Content = content;
var response = await client.SendAsync(request);
response.EnsureSuccessStatusCode();
Console.WriteLine(await response.Content.ReadAsStringAsync());

```

+++ Dart

```dart
var headers = {
  'Content-Type': 'application/json',
  'apikey': '[your api key]'
};
var request = http.Request('POST', Uri.parse('https://api.sociocs.com/message'));
request.body = json.encode({
  "provider": "[provider]",
  "channel_key": "[your channel key]",
  "to": "[phone number]",
  "name": "[recipient name]",
  "image_urls": [
    "[image url 1]",
    "[image url 2]",
    "[image url 3]"
  ]
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

  url := "https://api.sociocs.com/message"
  method := "POST"

  payload := strings.NewReader(`{`+"
"+`
    "provider": "[provider]",`+"
"+`
    "channel_key": "[your channel key]",`+"
"+`
    "to": "[phone number]",`+"
"+`
    "name": "[recipient name]",`+"
"+`
    "image_urls": [`+"
"+`
        "[image url 1]",`+"
"+`
        "[image url 2]",`+"
"+`
        "[image url 3]"`+"
"+`
    ]`+"
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
  req.Header.Add("apikey", "[your api key]")

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
RequestBody body = RequestBody.create(mediaType, "{\r\n    \"provider\": \"[provider]\",\r\n    \"channel_key\": \"[your channel key]\",\r\n    \"to\": \"[phone number]\",\r\n    \"name\": \"[recipient name]\",\r\n    \"image_urls\": [\r\n        \"[image url 1]\",\r\n        \"[image url 2]\",\r\n        \"[image url 3]\"\r\n    ]\r\n}");
Request request = new Request.Builder()
  .url("https://api.sociocs.com/message")
  .method("POST", body)
  .addHeader("Content-Type", "application/json")
  .addHeader("apikey", "[your api key]")
  .build();
Response response = client.newCall(request).execute();
```

+++ Node.js

```javascript
// This sample uses Axios library
const axios = require('axios');
let data = JSON.stringify({
  "provider": "[provider]",
  "channel_key": "[your channel key]",
  "to": "[phone number]",
  "name": "[recipient name]",
  "image_urls": [
    "[image url 1]",
    "[image url 2]",
    "[image url 3]"
  ]
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://api.sociocs.com/message',
  headers: { 
    'Content-Type': 'application/json', 
    'apikey': '[your api key]'
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
  'apikey' => '[your api key]'
];
$body = '{
  "provider": "[provider]",
  "channel_key": "[your channel key]",
  "to": "[phone number]",
  "name": "[recipient name]",
  "image_urls": [
    "[image url 1]",
    "[image url 2]",
    "[image url 3]"
  ]
}';
$request = new Request('POST', 'https://api.sociocs.com/message', $headers, $body);
$res = $client->sendAsync($request)->wait();
echo $res->getBody();
```

+++ Python

```python
# This sample uses Requests library
import requests
import json

url = "https://api.sociocs.com/message"

payload = json.dumps({
  "provider": "[provider]",
  "channel_key": "[your channel key]",
  "to": "[phone number]",
  "name": "[recipient name]",
  "image_urls": [
    "[image url 1]",
    "[image url 2]",
    "[image url 3]"
  ]
})
headers = {
  'Content-Type': 'application/json',
  'apikey': '[your api key]'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

+++

### Response object examples

#### When the API call was successful

```json
{
    "status": "success"
}
```

#### When the API call was unsuccessful

```json
{
    "status": "error",
    "errors": [{ "msg": "Invalid channel_key." }]
}
```
