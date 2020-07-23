---
layout: default
title: preorder
parent: apis
nav_order: 6
---

# preorder

After end user intends to buy the package after detail is rendered, before transaction is complete, FMS requires the pre-order of the package in order to preserve a eSIM profile from the pool, refer to [`package/preOrderPackage`](http://47.56.82.232:49090/swagger-ui.html#/package-controller/preOrderPackageUsingPOST) for api details

## request

```json

{
  "currency": "string",
  "currencyId": 0,
  "deviceType": "string",
  "id": 0,
  "languageId": "string",
  "money": 0,
  "packageCode": "string",
  "partnerCode": "string",
  "periodNum": 0
}

```

## parameters

1. 




## response


---
