# Place an order

```plaintext--prod
POST https://rest.lalamove.com/v2/orders
```

```plaintext--sandbox
POST https://sandbox-rest.lalamove.com/v2/orders
```

> Body

```js
{
  "quotedTotalFee": { "amount": "108000", "currency": "THB" },
  "callerSideCustomerOrderId": "YOUR_UNIQUE_REF",
  "sms": false,
  // ... merge with body used for quotation
}
```

> <aside class="warning">
> <b>IMPORTANT:</b> Merge the above with the <code>body</code> that was used for <a href="#get-a-quotation">requesting quotation</a>.
> </aside>

> **Responses**

> `201`
> Order Created

```json
{
  "customerOrderId": <LALAMOVE_ORDER_ID>,
  "orderRef": <LALAMOVE_ORDER_REF>
}
```

> `402`
> You have insufficient credit. Please [top up](https://web.lalamove.com/)

```json
{ "message": "ERR_INSUFFICIENT_CREDIT" }
```

> `409`
> The currency you provided in `quotedTotalFee.currency` is not a valid currency

```json
{ "message": "ERR_INVALID_CURRENCY" }
```

> `409`
> The amount or currency you provided in `quotedTotalFee` doesn't match quotation

```json
{ "message": "ERR_PRICE_MISMATCH" }
```

> `429`
> Too Many Requests

```js
// no body
```

`POST` `/v2/orders`

Provide the `totalFee` and `totalFeeCurrency` received from `/quotations` as `quotedTotalFee.amount` and `quotedTotalFee.currency` merged with the exact same body used for `/quotations`.

<aside class="notice">The <code>amount</code> and <code>currency</code> of <code>quotedTotalFee</code> <b>MUST</b> match with quotation.</aside>

**Body**

|                             |     |           |                                                                          |
| --------------------------- | --- | --------- | ------------------------------------------------------------------------ |
| `quotedTotalFee.amount`     |     | `string`  | `totalFee` from `/quotations`                                            |
| `quotedTotalFee.currency`   |     | `string`  | `totalFeeCurrency` from `/quotations`                                    |
| `callerSideCustomerOrderId` | 🤷‍♀️  | `string`  | Used for associating your data with Lalamove's order. eg. your order id. |
| `sms`                       | 🤷‍♀️  | `boolean` | Send delivery updates SMS to **ALL** recipients. Default to `true`       |

🤷‍♀️ - _Optional_
