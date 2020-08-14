---
layout: default
title: webhook
parent: apis
nav_order: 9
---

# payment webhook

After transanction is complete, the application should inform FMS so that the eSIM QR profile is assigned to the order. Please refer to [`/payment/webhook`](http://47.56.82.232:49090/swagger-ui.html#/pay-stripe-for-p-002275-controller/webhookUsingPOST) for api details

## request

```json

{
  "dateTime": 1,
  "orderId": "string",
  "partnerCode": "string",
  "payAmount": 100,
  "payCurrency": "USD",
  "paypalId": "string",
  "type": "payment_intent.succeeded"
}

```

### parameters

1. **`dataTime`** is the seconds of the transaction time in the transaction timezone.

2. **`orderId`** is the `id` returned by `pacakge/preOrderPackage`

3. **`type`** is the result of the payment transaction

4. **`payCurrency`**: `USD`

- `payment_intent.succeeded`
- `payment_intent.payment_failed`

## Response

### code

`0`:success; `2`:Wrong parameters; `1102`:Time conversion exception; `9999`:Error;  `6006`:pre-order timeout;
`10008`: order does not exist; `10009`: price inconsistent
`3004`: order system exception; `3005`: qrCode null
others: system exception

- `6006`: if the transaction result is notified more than **`10`** minutes after preOrder is called, this notificaion is considered _timeout_.

_example_:

```json
{
    "code": 10008,
    "data": null,
    "message": "paypal The callback has no order number"
}

```

```json
{
    "code": 6006,
    "data": null,
    "message": "PreOrder Timeout"
}
```

---
