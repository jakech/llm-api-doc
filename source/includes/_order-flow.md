# Order flow

![order-flow](images/order-flow.svg)

### Driver rejection

Order can be rejected after matched. When that happens, order status will be reverted from `ON_GOING` to `ASSIGNING_DRIVER` and we will try to match it again with a different driver. When an order is rejected a second time, the order status will change to `REJECTED` and we will no longer try to find a match for that order.
