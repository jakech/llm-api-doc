# Cancel an order

```
PUT https://rest.lalamove.com/v2/orders/{id}/cancel
```

> Headers

```yaml
Authorization: hmac <TOKEN>
Content-Type: application/json
X-LLM-Country: <YOUR_COUNTRY>
X-Request-ID: <NONCE>
```

> Responses: `200`

```js
{}
```

`PUT` `/v2/orders/{id}/cancel`

Cancellation, blah blah blah.

**URL Params**

|      |                       |
| ---- | --------------------- |
| `id` | `<LALAMOVE_ORDER_ID>` |
