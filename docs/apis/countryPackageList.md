---
layout: default
title: countryPackageList
parent: apis
nav_order: 3
---

# countryPackageList

To query all the available countries (the data plans covering countries) assigned to this enterprise account

## Request Parameters

```json
{
  "countryCode": 460,
  "languageId": "string",
  "pageNum": 0,
  "pageSize": 0,
  "partnerCode": "P001101",
  "type": 2
}
```

please note that:

1. ~~`pageNum`~~ and ~~`pageSize`~~ are not in use anymore.
All the countries assigned to the `partnerCode` (the enterprise) will be returned in the response

2. `type`: `1`:The package coverage list includes this country; `2`:The package only covers this country

3. `countryCode` is in format of the ISO MCC (Mobile Country Code)

---


