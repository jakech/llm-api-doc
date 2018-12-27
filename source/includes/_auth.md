# Authentication

Lalamove API makes use of [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code) (SHA256) as the authentication mechanism.

You will be provided an api `KEY`, and a `SECRET` for generating a [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code) hash (also known as a `SIGNATURE`).

## Signature

> JavaScript

```js
const SECRET = 'MCwCAQACBQDDym2lAgMBAAECBDHB';

const time = new Date().getTime().toString(); // `1545880607433`

const method = 'POST';
const path = '/v2/quotations';
const body = JSON.stringify({...}); // the whole body for '/v2/quotations'
const rawSignature = `${time}\r\n${method}\r\n${path}\r\n\r\n${body}`;

const signature = CryptoJS.HmacSHA256(rawSignature, SECRET);
```

`SIGNATURE = HmacSHA256(<TIMESTAMP>\r\n<HTTP_VERB>\r\n<PATH>\r\n\r\n<BODY>, <SECRET>)`

|             |                                                                                 |
| ----------- | ------------------------------------------------------------------------------- |
| `SECRET`    | You API secret                                                                  |
| `TIMESTAMP` | _Unix_ timestamp in millisecond eg. `1545880607433`                             |
| `HTTP_VERB` | _HTTP_ verb (`GET`, `POST`, `PUT`, `DELETE`) of the specific API call           |
| `PATH`      | The _pathname_ of the specific API call including version. eg. `/v2/quotations` |
| `BODY`      | The request body in _JSON string_                                               |

## Headers

> <aside class="notice">Every call <b>MUST</b> include the following headers</aside>

```yaml
Authorization: hmac <TOKEN>
Content-Type: application/json
X-LLM-Country: <YOUR_COUNTRY>
X-Request-ID: <NONCE> # TODO
```

`TOKEN = <KEY>:<TIMESTAMP>:<SIGNATURE>`

|             |                                                                                  |
| ----------- | -------------------------------------------------------------------------------- |
| `KEY`       | Your API key                                                                     |
| `TIMESTAMP` | **MUST** be identical to `TIMESTAMP` in [`SIGNATURE`](#authentication-signature) |
| `SIGNATURE` | [As generated here](#authentication-signature)                                   |
