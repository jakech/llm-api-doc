# Get order details

```
GET https://rest.lalamove.com/v2/orders/{id}
```

> Headers

```yaml
Authorization: hmac <TOKEN>
Content-Type: application/json
X-LLM-Country: <YOUR_COUNTRY>
X-Request-ID: <NONCE>
```

> Responses: `200`

```json
{
  "driverId": "8799752",
  "status": "COMPLETED" // TODO
}
```

`GET` `/v2/orders/{id}`

Blah blah blah.

**URL Params**

|      |                       |
| ---- | --------------------- |
| `id` | `<LALAMOVE_ORDER_ID>` |

## Get driver details

```
GET https://rest.lalamove.com/v2/orders/{orderId}/drivers/{driverId}
```

> Headers

```yaml
Authorization: hmac <TOKEN>
Content-Type: application/json
X-LLM-Country: <YOUR_COUNTRY>
X-Request-ID: <NONCE>
```

> Responses: `200`

```json
{
  "name": "David",
  "phone": "+668912121212"
}
```

`GET` `/v2/orders/{orderId}/drivers/{driverId}`

Blah blah blah.

**URL Params**

|            |                                        |
| ---------- | -------------------------------------- |
| `orderId`  | `<LALAMOVE_ORDER_ID>`                  |
| `driverId` | `driverId` from `/orders/{id}` response |
