# Order flow

![status](images/status-flow.svg)

### Driver rejection

Driver can reject an order after matched. When that happens, order status will be reverted from `ON_GOING` to `ASSIGNING_DRIVER` and we will try to match it again with a different driver. When a second driver also rejects the order, the order status will change to `REJECTED` and we will no longer try to match that order.
