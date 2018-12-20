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

```js
{
  "driverId": "8799752",
  "status": "COMPLETED"
  "price": {
    "amount": "253",
    "currency": "THB"
  }
}
```

`GET` `/v2/orders/{id}`

Blah blah blah.

**URL Params**

|      |                       |
| ---- | --------------------- |
| `id` | `<LALAMOVE_ORDER_ID>` |

**Order Status**

|             |                                                     |
| ----------- | --------------------------------------------------- |
| `ASSIGNING` | Trying to match shipment with a driver              |
| `ONGOING`   | Shipment is matched with a driver                   |
| `CANCELLED` | Shipment is cancelled before pick up                |
| `REJECTED`  | Shipment was matched and later reverted             |
| `PICKED_UP` | Shipment is picked up by the driver                 |
| `COMPLETED` | Sucessfully delivered and transaction has concluded |
| `EXPIRED`   | Order expired because a match could not be found    |

## Driver details

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

```js
{
  "name": "David",
  "phone": "+668912121212"
}
```

`GET` `/v2/orders/{orderId}/drivers/{driverId}`

Blah blah blah.

**URL Params**

|            |                                         |
| ---------- | --------------------------------------- |
| `orderId`  | `<LALAMOVE_ORDER_ID>`                   |
| `driverId` | `driverId` from `/orders/{id}` response |

## Driver location

```
GET https://rest.lalamove.com/v2/orders/{orderId}/drivers/{driverId}/location
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
{
  "location": { "lat": "13.740167", "lng": "100.535237" },
  "updatedAt": "2017-12-01T14:30.00Z"
}
```

`GET` `/v2/orders/{orderId}/drivers/{driverId}/location`

Blah blah blah.

**URL Params**

|            |                                         |
| ---------- | --------------------------------------- |
| `orderId`  | `<LALAMOVE_ORDER_ID>`                   |
| `driverId` | `driverId` from `/orders/{id}` response |
