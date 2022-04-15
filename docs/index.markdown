---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
nav_order: 1
---
# Introduction

FMS is the eSIM QR provisiong and online store management system made available to enterpise eSIM customers, powered by Linksfield Network.

## Versions

__FMS APP API v1.1__
1. removed the api access_token (in request header) for apis:
- /package/packageList,
- /package/queryCountry,
- /package/countryPackageList,
- /package/selectContinentsCode,
- /package/selectPackageByContinents,
- /package/selectHotPackage,
- /package/detail

2. added topup feature to top up the already purchased eSIM
/package/topUpOrder
/package/selectTopUpList

3. added (`2022 Apr 14`):
- /v1.1/package/packageList
- /v1.1/package/detail
- /v1.1/package/preOrderPackage
- /v1.1/order/myEsimDetail

__FMS APP API v1.0__

## Scope

This document defines the interface between the enterprise backend system or App, and the FMS platform to render connectivity control, and eSIM data bundle management to the enterprise users.

## Char set

`UTF-8` encoding is used by default

## Swagger

Please refer to [Swagger API](https://swaggertest.linksfield.net/fms/swagger-ui.html) for details of these APIs.

Please note that:
1. for easy manipulation of the request header parameters, it is recommended to use *postman* for actual testing.
2. swagger api is in testing environment.


## Important Notice

Deprecated Parameters
{: .label .label-red }

- `pageNum`
- `pageSize`
- `verifyCode`
- `orderNum`

---
[Get Started](general/){: .btn .btn-purple }
