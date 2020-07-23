---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
nav_order: 3
permalink: /flow/
---

# Flow

{: .no_toc}

FMS APIs system renders 3 modules, user, package and order. Payment gateway integration or implementation is not within the scope of this document.

---

## Table of contents

{: .no_toc .text-delta}

1. TOC
{:toc}

## Flow general

In this chapter, some typical flows will be described. 

---

### A complete flow

The apis flow of a typical successful purchase of eSIM QR profile is as below:

| No. of step | description | API used|
|:------------|:------------|:----------------------|
| 1           | register or authenticate user to get access to apis        | /user/emailRegister or /user/login  |
| 2           | query  country list         | package/countryPackageList         |
| 3           | query package by country         | /package/packageList         |
| 4           | query data package detail        |   /package/detail   |
| 5           | call this api to create order and reserve the QR profile for the user. It will return orderId for you to pay       |   /package/preOrderPackage    |
| 6           |  pay with the orderId obtained from the previous step  | N.A. ( enterprise completes the payment)  |
| 7           |  call this api after successful payment with loop, until orderPayStatus returned by this api is not 0  |  /package/queryOrdStatusAndEmail  |

---

### Update password flow

By default, the user registration and management is handled by enterprise's own app and backend services. But in order to associate the user with the eSIM QR profile order, FMS is to be informed of the user changes. 

In the event of the password being changed or being reset by end users, new password is to be synced with FMS for 

_to be added_

---

### Notification of successful payment


---
[back to **general**](/fms-api/general){: .btn .btn-green .mr-4}            [next to **api**](/fms-api/apis/){: .btn .btn-purple }