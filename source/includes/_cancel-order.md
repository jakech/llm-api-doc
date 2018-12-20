# Cancel an order

```
PUT https://rest.lalamove.com/v2/orders/{customerOrderId}/cancel
```

> Headers

```yaml
Authorization: hmac <TOKEN>
Content-Type: application/json
X-LLM-Country: <YOUR_COUNTRY>
X-Request-ID: <NONCE>
```

> Body

```json
{}
```

> Responses: `200`

```json
{}
```

`PUT` `/v2/orders/{id}/cancel`

Cancellation, blah blah blah.

**URL Params**

|      |     |          |                |
| ---- | --- | -------- | -------------- |
| `id` | ✅  | `string` | blah blah blah |

✅ - _Required_
