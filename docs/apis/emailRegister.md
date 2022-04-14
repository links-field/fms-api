---
layout: default
title: emailRegister
parent: apis
nav_order: 2
---

# emailRegister

while enterprise backend handles their own user registration flow, it is important to inform FMS system to create an account for this user and associate it with a valid email address, for future order, notification and updates. Refer to [/user/emailRegister](http://47.56.82.232:49090/swagger-ui.html#/user-controller/registerUsingPOST) for detail.

## request

```json
{
  "appId": 12,
  "email": "xieguocheng_2006@163.com",
  "partnerCode": "P001101",
  "passwd": "6e99d95b538ad2db523f17c68fe961c5",
  "userType": 4,
  "verifyCode": 3206
}
```

## parameters

1. `password` is MD5 processed
2. ~~`verfiyCode`~~ is not in use


## response

`x-access-token` will be returned in the response, it is required to carry this token in the header of following APIs. Token expires in 



