# Get order details

```plaintext--prod
GET https://rest.lalamove.com/v2/orders/{id}
```

```plaintext--sandbox
GET https://sandbox-rest.lalamove.com/v2/orders/{id}
```

> **Responses**

> `200` `ASSIGNING_DRIVER`

```json
{
  "driverId": "",
  "status": "ASSIGNING_DRIVER",
  "price": {
    "amount": "108000",
    "currency": "THB"
  }
}
```

> `200` `ON_GOING`

```json
{
  "driverId": "33522",
  "status": "ON_GOING",
  "price": {
    "amount": "158000",
    "currency": "IDR"
  }
}
```

> `200` `CANCELED`

```json
{
  "driverId": "",
  "status": "CANCELED",
  "price": {
    "amount": "158000",
    "currency": "IDR"
  }
}
```

> `200` `PICKED_UP`

```json
{
  "driverId": "33522",
  "status": "PICKED_UP",
  "price": {
    "amount": "156000",
    "currency": "IDR"
  }
}
```

> `200` `COMPLETED`

```json
{
  "driverId": "8799752",
  "status": "COMPLETED"
  "price": {
    "amount": "108000",
    "currency": "THB"
  }
}
```

> `200` `EXPIRED`

```json
{
  "driverId": "",
  "status": "EXPIRED",
  "price": {
    "amount": "108000",
    "currency": "THB"
  }
}
```

`GET` `/v2/orders/{id}`

**URL Params**

|      |                       |
| ---- | --------------------- |
| `id` | `<LALAMOVE_ORDER_ID>` |

### Order Status

![status](images/status-flow.svg)

|                    |                                                     |
| ------------------ | --------------------------------------------------- |
| `ASSIGNING_DRIVER` | Trying to match shipment with a driver              |
| `ON_GOING`         | Shipment is matched with a driver                   |
| `CANCELLED`        | Shipment is cancelled before pick up                |
| `PICKED_UP`        | Shipment is picked up by the driver                 |
| `REJECTED`         | Shipment was matched and later reverted             |
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

Retrieve driver's name and phone number.

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

Retrieve driver's lastest location in latitude and longitude.

**URL Params**

|            |                                         |
| ---------- | --------------------------------------- |
| `orderId`  | `<LALAMOVE_ORDER_ID>`                   |
| `driverId` | `driverId` from `/orders/{id}` response |
