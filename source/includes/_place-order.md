# Place an order

```plaintext--prod
POST https://rest.lalamove.com/v2/orders
```

```plaintext--sandbox
POST https://sandbox-rest.lalamove.com/v2/orders
```

> Headers

```yaml
Authorization: hmac <TOKEN>
Content-Type: application/json
X-LLM-Country: <YOUR_COUNTRY>
X-Request-ID: <NONCE> # TODO
```

> Body

```js
{
  "quotedTotalFee": {
    "amount": "67",
    "currency": "SGD"
  },
  "callerSideCustomerOrderId": <YOUR_UNIQUE_REF>,
  "sms": false,
  // ... merge with body used for quotation
}
```

> <aside class="warning">
> <b>IMPORTANT:</b> Merge the above with the <code>body</code> that was used for <a href="#get-a-quotation">requesting quotation</a>.
> </aside>

> Responses: `201`

```js
{
  "customerOrderId": <LALAMOVE_ORDER_ID>,
  "orderRef": <LALAMOVE_ORDER_REF>
}
```

`POST` `/v2/orders`

Use the fee received from `/quotations` Blah blah blah.

<aside class="notice">The amount and currency of <code>quotedTotalFee</code> <b>MUST</b> match with quotation.</aside>

**Body**

|                             |     |           |                                                                    |
| --------------------------- | --- | --------- | ------------------------------------------------------------------ |
| `quotedTotalFee.amount`     | ✅  | `string`  | blah blah blah                                                     |
| `quotedTotalFee.currency`   | ✅  | `string`  | adada                                                              |
| `callerSideCustomerOrderId` |     | `string`  | adad, example usecase                                              |
| `sms`                       |     | `boolean` | Send delivery updates SMS to **all** recipients. Default to `true` |

✅ - _Required_
