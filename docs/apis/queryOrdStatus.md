---
layout: default
title: queryOrdStatus
parent: apis
nav_order: 7
---

# queryOrdStatusAndEmail

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

1. `id` is the id of the selected data package
2. `orderNum` is how many of the same data package are to be ordered  

_description pending_


## response


---
