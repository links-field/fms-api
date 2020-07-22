---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
nav_order: 2
permalink: /general/
---

# General

{: .no_toc}

FMS APIs system renders 3 modules, user, package and order. Payment gateway integration or implementation is not within the scope of this document.

## Table of contents

{: .no_toc .text-delta}

1. TOC
{:toc}

## API Request

API request body is comprised of parameters that are used to request information from FMS platform

### request header

After registeration or successful login, Api access token will be returned in the response. Embed the token in the header of the following APIs.

### sample

```json
//sample code 
{
  "countryCode": 460,
  "languageId": "string",
  "pageNum": 0,
  "pageSize": 0,
  "partnerCode": "P001101",
  "type": 2
}

```

### parameters

Across the APIs, below are the common parameters and their descriptions:

| Parameter   | Is Required | Descriptions/ Remarks |
|:------------|:------------|:----------------------|
| partnerCode        | Yes         | Enterprise code, 'p' followed by 6 digits, for example `P001101` |
| type        | Yes         | Response data         |
| userType        | Yes         | system administrator:1; Enterprise user:2; business user:3; customer:4    |
| appId     | Yes         | app: 12;The background: 10; H5: 14 |

## Response

Reponse usually follows below format:

```json

{
  "code": 0,
  "data": {},
  "message": "string",
  "messageSourceHandler": {}
}

```

| Parameter   | Is Required | Descriptions/ Remarks |
|:------------|:------------|:----------------------|
| code        | Yes         | `0000` means success  |
| data        | Yes         | Response data         |
| message        | Yes         | response message     |
| messageSourceHandler     | Yes         |   -    |

## Flow

The apis flow of a successful order is as below:

| No. of step | description | API used|
|:------------|:------------|:----------------------|
| 1           | register or authenticate user to get access to apis        | /user/emailRegister or /user/login  |
| 2           | query package by country         | package/countryPackageList         |
| 3           | query data package detail        |   /package/detail   |
| 4           | after user clicks on 'pay' button, before actual transaction is complete, call this api to reserve the QR profile for the user          |   /package/preOrderPackage    |
| 5           |   |
