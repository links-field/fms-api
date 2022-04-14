---
layout: default
title: packageList
parent: apis
nav_order: 4
---

# packageList

After selecting a country, get all the avaiable data packages that covers this country. The country coverage can be configured in FMS portal.
**Actual covering countries** are not necessarily the same as the **country list**. For example, a global data package that actually covers 67 countries, through configuration in FMS portal, this data package can only be seen under 3 countries. Refer to [package/packageList](http://47.56.82.232:49090/swagger-ui.html#/package-controller/packageListUsingPOST) for detail.

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

1. ~~`pageNum`~~ and ~~`pageSize`~~ are not in use anymore. all the available packages are to be returned in the response.
2. when `countryCode` and `isoCountryName` both exist in parameters, `countryCode` supercedes.
3. `type` is mandatory, the value is either `1` or `2`. refer to [countryPackageList](/fms-api/apis/countryPackageList/#request-parameters) for meaning of `type`.


## response



