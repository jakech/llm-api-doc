# Authentication

Lalamove API makes use of [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code) (SHA256) as the authentication mechanism.

You will be provided an api `KEY`, and a `SECRET` for generating a [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code) hash (also known as a `SIGNATURE`).

## Signature

> Example in JavaScript

```js
const SECRET = 'MCwCAQACBQDDym2lAgMBAAECBDHB';
const time = new Date().getTime().toString(); // => `1545880607433`

const method = 'POST';
const path = '/v2/quotations';
const body = JSON.stringify({...}); // => the whole body for '/v2/quotations'

const rawSignature = `${time}\r\n${method}\r\n${path}\r\n\r\n${body}`;
// => '1546222219293\r\nPOST\r\n/v2/quotations\r\n\r\n{\n \"scheduleAt\": \"2018-12-31T14:30:00.00Z\",\n \"serviceType\": \"MOTORCYCLE\",\n \"requesterContact\": { \"name\": \"Peter Pan\", \"phone\": \"232\" },\n \"stops\": [\n {\n \"location\": { \"lat\": \"-6.255431000000001\", \"lng\": \"106.60114290000001\" },\n \"addresses\": {\n \"en_ID\": {\n \"displayString\":\n \"Jl. Perum Dasana Indah No.SD 3/ 17-18, RT.3/RW.1, Bojong Nangka, Klp. Dua, Tangerang, Banten 15810, Indonesia\",\n \"country\": \"ID\"\n }\n }\n },\n {\n \"location\": { \"lat\": \"-6.404722800000001\", \"lng\": \"106.81902130000003\" },\n \"addresses\": {\n \"en_ID\": {\n \"displayString\": \"Jl. Kartini, Ruko No. 1E, Depok, Pancoran MAS, Kota Depok, Jawa Barat 16431, Indonesia\",\n \"country\": \"ID\"\n }\n }\n }\n ],\n \"deliveries\": [\n {\n \"toStop\": 1,\n \"toContact\": {\n \"name\": \"mm\",\n \"phone\": \"9999999\"\n }\n }\n ]\n}\n'

const SIGNATURE = CryptoJS.HmacSHA256(rawSignature, SECRET).toString();
// => '5133946c6a0ba25932cc18fa3aa1b5c3dfa2c7f99de0f8599b28c2da88ed9d42'
```

<aside class="warning">
A unique <b>Signature Hash</b> has to be generated for <b>EVERY</b> API call at the time of making such call.
</aside>

`SIGNATURE = HmacSHA256(<TIMESTAMP>\r\n<HTTP_VERB>\r\n<PATH>\r\n\r\n<BODY>, <SECRET>)`

|             |                                                                                 |
| ----------- | ------------------------------------------------------------------------------- |
| `SECRET`    | You API secret                                                                  |
| `TIMESTAMP` | _Unix_ timestamp in millisecond eg. `1545880607433`                             |
| `HTTP_VERB` | _HTTP_ verb (`GET`, `POST`, `PUT`, `DELETE`) of the specific API call           |
| `PATH`      | The _pathname_ of the specific API call including version. eg. `/v2/quotations` |
| `BODY`      | The request body in _JSON string_                                               |

Also see

* [Examples of creating base64 hashes using HMAC SHA256 in different languages](https://www.jokecamp.com/blog/examples-of-creating-base64-hashes-using-hmac-sha256-in-different-languages)

## Headers

> Example in JavaScript **(cont.)**

```js
const API_KEY = '914c9e52e6414d9494e299708d176a41'
const TOKEN = `${API_KEY}:${time}:${SIGNATURE}`
// => '914c9e52e6414d9494e299708d176a41:1545880607433:5133946c6a0ba25932cc18fa3aa1b5c3dfa2c7f99de0f8599b28c2da88ed9d42'
```

> <aside class="warning">Every call <b>MUST</b> include the following headers.</aside>

```yaml
Authorization: hmac <TOKEN>
X-LLM-Country: <YOUR_COUNTRY>
X-Request-ID: <NONCE>
```

> Example

```yaml
Authorization: hmac 914c9e52e6414d9494e299708d176a41:1545880607433:5133946c6a0ba25932cc18fa3aa1b5c3dfa2c7f99de0f8599b28c2da88ed9d42
X-LLM-Country: TH
X-Request-ID: 211b9d85-a2cc-476f-8675-b61ec923cc27
```

### Authorization

`TOKEN = <KEY>:<TIMESTAMP>:<SIGNATURE>`

|             |                                                                                  |
| ----------- | -------------------------------------------------------------------------------- |
| `KEY`       | Your API key                                                                     |
| `TIMESTAMP` | **MUST** be identical to `TIMESTAMP` in [`SIGNATURE`](#authentication-signature) |
| `SIGNATURE` | As described in [Signature](#authentication-signature)                           |

### X-LLM-Country

The country the requested service is for, in [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) format. [See Available countries](#available-countries)

<aside class="notice">
Currently, API keys are limited to a <b>single country/region</b>.
</aside>

<aside class="success"><a href="#sales">Contact us</a> if you would like to expand your operations to more countries and regions.</aside>

### X-Request-ID

Provide a [Nonce](https://en.wikipedia.org/wiki/Cryptographic_nonce) to be used as an unique Request ID. It helps us with preventing replay attacks.
