# Place an order

```
POST https://rest.lalamove.com/v2/orders
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
{
  "quotedTotalFee": {
    "amount": "67",
    "currency": "SGD"
  },
  "callerSideCustomerOrderId": <YOUR_UNIQUE_REF>,
  "sms": false,
  ...
}
```

> <aside class="warning">
> <b>IMPORTANT:</b> Merge the above with the <code>body</code> that was used for <a href="#get-a-quotation">requesting quotation</a>.
> </aside>

> Responses: `201`

```json
{
  "customerOrderId": <YOUR_UNIQUE_REF>,
  "orderRef": "179802"
}
```

`POST` `/v2/orders`

Use the fee received from `/quotations` Blah blah blah.

**Body**

<aside class="notice">The amount and currency of <code>quotedTotalFee</code> <b>MUST</b> match with quotation.</aside>

|                             |     |           |                                                                    |
| --------------------------- | --- | --------- | ------------------------------------------------------------------ |
| `quotedTotalFee.amount`     | ✅  | `string`  | blah blah blah                                                     |
| `quotedTotalFee.currency`   | ✅  | `string`  | adada                                                              |
| `callerSideCustomerOrderId` |     | `string`  | adad, example usecase                                              |
| `sms`                       |     | `boolean` | Send delivery updates SMS to **all** recipients. Default to `true` |

✅ - _Required_
