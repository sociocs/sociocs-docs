---
title: Authentication
order: -150
---

API calls are authenticated using API key.

### Generating API key

To generate API key, go to *Profile & settings -> API* on <a href="https://app.sociocs.com" target="_blank">app.sociocs.com</a>.

### Using the key in API calls

There are multiple ways to send API key with the request.

#### 1. "apikey" header [!badge Recommended]

Pass a request header `apikey` with your account's API key as value.

For example, if your API key is `e047nbp2UnWuHD9m:Xqc37DHPGMyF0Z4hWX3Afn1Iyj6j7dPc`, you can send the  `apikey` in the request headers like below.

+++ cURL

```shell
curl --location 'https://api.sociocs.com' --header 'apikey: e047nbp2UnWuHD9m:Xqc37DHPGMyF0Z4hWX3Afn1Iyj6j7dPc'
```

+++

#### 2. Basic authorization

The generated API key has two parts with a `:` in between. You can use the value before `:` as `Username`, and value after as `Password`.

For example, if your API key is `e047nbp2UnWuHD9m:Xqc37DHPGMyF0Z4hWX3Afn1Iyj6j7dPc`, you can use `e047nbp2UnWuHD9m` as `Username` and `Xqc37DHPGMyF0Z4hWX3Afn1Iyj6j7dPc` as `Password`.

#### 3. Basic authorization in the URL [!badge variant="warning" text="Not recommended"]

*You should use this approach only when sending a header in the request is not possible.*

You can use the API BASE URL in this format to send the key with the request `https://[your-api-key]@api.sociocs.com/...`.

For example, if you are calling the `Send message` API, and your API key is `e047nbp2UnWuHD9m:Xqc37DHPGMyF0Z4hWX3Afn1Iyj6j7dPc`, you can use the API URL as `https://e047nbp2UnWuHD9m:Xqc37DHPGMyF0Z4hWX3Afn1Iyj6j7dPc@api.sociocs.com/message`.

+++ cURL

```shell
curl --location 'https://e047nbp2UnWuHD9m:Xqc37DHPGMyF0Z4hWX3Afn1Iyj6j7dPc@api.sociocs.com'
```

+++

#### 4. Query string [!badge variant="danger" text="Insecure"]

*This approach is considered insecure because the API key is part of the URL and can be logged by the interim systems.*

You can send the API key as query string parameter like this `https://api.sociocs.com/...?apikey=[your-api-key]`.

For example, if you are calling the `Send message` API, and your API key is `e047nbp2UnWuHD9m:Xqc37DHPGMyF0Z4hWX3Afn1Iyj6j7dPc`, you can pass API key in the URL like this `https://api.sociocs.com/message?apikey=e047nbp2UnWuHD9m:Xqc37DHPGMyF0Z4hWX3Afn1Iyj6j7dPc`.

+++ cURL

```shell
curl --location 'https://api.sociocs.com/message?apikey=e047nbp2UnWuHD9m:Xqc37DHPGMyF0Z4hWX3Afn1Iyj6j7dPc'
```

+++
