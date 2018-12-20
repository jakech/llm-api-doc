# Get order details

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
