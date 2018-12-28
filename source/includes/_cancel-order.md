# Cancel an order

```plaintext--prod
PUT https://rest.lalamove.com/v2/orders/{id}/cancel
```

```plaintext--sandbox
PUT https://sandbox-rest.lalamove.com/v2/orders/{id}/cancel
```

> **Responses**

> `200`

```json
{}
```

> `409`
> Cancellation does not meet certain constraints **WHAT constraints? @Pat**

```json
{ "message": "ERR_CANCELLATION_FORBIDDEN" }
```

`PUT` `/v2/orders/{id}/cancel`

Cancellation, blah blah blah. When am I not allow to cancel????? @Pat


**URL Params**

|      |                       |
| ---- | --------------------- |
| `id` | `<LALAMOVE_ORDER_ID>` |
