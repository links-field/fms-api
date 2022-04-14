---
layout: default
title: detail
parent: apis
nav_order: 5
---

# detail

After selecting a package, details of this package is returned using [`package/detail`](http://47.56.82.232:49090/swagger-ui.html#/package-controller/detailUsingGET) api

## request

```json
{
  "id": ,
  "orderNumber": 1
}
```

## parameters

1. `id` is the id of the selected data package
2. ~~`orderNum`~~ is deprecated, it indicates how many of this data package are to be ordered, and is **Ignored** in current system.


## response

```json
{
  "code": 0,
  "data": {
    "buyType": 2,
    "configFlag": "string",
    "coverCountrys": 460,
    "currencyIds": "string",
    "currencyInfos": [
      {
        "currencyAbbr": "string",
        "currencyId": 0,
        "currencyName": "string",
        "currencySymbol": "string",
        "digitsNum": "string",
        "price": 0,
        "unit": "string"
      }
    ],
    "id": 0,
    "logo": "string",
    "maxOrderPeriod": 2,
    "minOrderPeriod": 2,
    "packageCode": "string",
    "packageDesc": "string",
    "packageFlow": 2,
    "packageId": "string",
    "packageShortDesc": "亚洲",
    "packageShowName": "爱谁谁买套餐",
    "packageType": 2,
    "period": 0,
    "periodUnit": "string",
    "priceType": 2,
    "saleCount": "string",
    "surplusFlow": "string",
    "updateTime": "string"
  },
  "message": "string",
  "messageSourceHandler": {}
}



```

