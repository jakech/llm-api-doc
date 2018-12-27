# Get order details

```plaintext--prod
GET https://rest.lalamove.com/v2/orders/{id}
```

```plaintext--sandbox
GET https://sandbox-rest.lalamove.com/v2/orders/{id}
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

**Order Status (need to confirm)**

|                    |                                                     |
| ------------------ | --------------------------------------------------- |
| `ASSIGNING_DRIVER` | Trying to match shipment with a driver              |
| `ONGOING`          | Shipment is matched with a driver                   |
| `CANCELLED`        | Shipment is cancelled before pick up                |
| `REJECTED`         | Shipment was matched and later reverted             |
| `PICKED_UP`        | Shipment is picked up by the driver                 |
| `COMPLETED`        | Sucessfully delivered and transaction has concluded |
| `EXPIRED`          | Order expired because a match could not be found    |

## Driver details

```plaintext--prod
GET https://rest.lalamove.com/v2/orders/{orderId}/drivers/{driverId}
```

```plaintext--sandbox
GET https://sandbox-rest.lalamove.com/v2/orders/{orderId}/drivers/{driverId}
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

```plaintext--prod
GET https://rest.lalamove.com/v2/orders/{orderId}/drivers/{driverId}/location
```

```plaintext--sandbox
GET https://sandbox-rest.lalamove.com/v2/orders/{orderId}/drivers/{driverId}/location
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
