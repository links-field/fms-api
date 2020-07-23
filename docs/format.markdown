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

| Parameter   | Type | Descriptions/ Remarks |
|:------------|:------------|:----------------------|
| partnerCode        | String         | Enterprise code, 'p' followed by 6 digits, for example `P001101` |
| type        | String         | Search Type  1： country; 2：region          |
| userType        | Integer         | system administrator:1; Enterprise user:2; business user:3; customer:4    |
| appId     | Integer         | app: 12;The background: 10; H5: 14 |

## API Response

Reponse usually follows below format:

```json

{
  "code": 0,
  "data": {},
  "message": "string",
  "messageSourceHandler": {}
}

```

| Parameter   | Type | Descriptions/ Remarks |
|:------------|:------------|:----------------------|
| code        | Integer        | `0` means success  |
| data        | Object         | Response data         |
| message        |    String      | Response message     |
| messageSourceHandler     |    Object       |   -    |


## Token

please refer to [emailRegister](/fms-api/apis/emailRegister) for token generation process.
It should be noted that:

- a new token will be generated each time with login
- a token is valid for 3 days
- after token expires, a login is required to get the new token
- api that uses expired token will receive error code `7` in response

---

[back to **introduction**](/fms-api/){: .btn .btn-green .mr-4}            [next to **flow**](/fms-api/flow/){: .btn .btn-purple }
