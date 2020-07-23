---
layout: default
title: packageList
parent: apis
nav_order: 3
---

# packageList

After selecting a country, get all the avaiable data packages that covers this country. The country coverage can be configured in FMS portal.
**Actual covering countries** are not necessarily the same as the **country list**. For example, a global data package that actually covers 67 countries, through configuration in FMS portal, this data package can only be seen under 3 countries.

## request

```json
{
  "countryCode": 460,
  "isoCountryName": "China",
  "languageId": "string",
  "pageNum": 0,
  "pageSize": 0,
  "partnerCode": "P001101",
  "type": 2
}
```

## parameters

1. 


## response


---
