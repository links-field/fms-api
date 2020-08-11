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
| 6           | pay with the orderId obtained from the previous step  | N.A. ( enterprise completes the payment)  |
| 7           | nofity FMS that the payment is successful  | webhook |
| 8           | call this api after successful payment, with loop, until orderPayStatus returned by this api is not 0  |  /package/queryOrdStatus  |
| 9           | get eSIM profile details | /order/myEsimDetail |


![flow-diagram](/payflow.png)

---

### Update password flow

By default, the user registration and management is handled by enterprise's own app and backend services. But in order to associate the user with the eSIM QR profile order, FMS is to be informed of the user changes. 

In the event of the password being changed or being reset by end users, new password is to be synced with FMS via [`/user/passwordReset`](http://47.56.82.232:49090/swagger-ui.html#/user-controller/passwordResetUsingPOST) api 

After the new password is set, it is required to [`/user/emailLogin`](http://47.56.82.232:49090/swagger-ui.html#/user-controller/emailLoginUsingPOST) to obtain a new token (in the response).

| No. of step | description | API used|
|:------------|:------------|:----------------------|
| 1           | change password or reset password    | n.a. (implemented by application server )  |
| 2           | change password sync with FMS        | user/passwordReset        |
| 3           | log in with FMS to authenticate user  | user/emailLogin           |

---

### Notification of successful payment

It is up to the enterprise business flow to complete a purchase of eSIM QR profile and transaction for the payment. But it is required that FMS is to be notified of the payment result, in order for the system to assign the actual eSIM profile for the order that has been paid successfully and correctly.  

The notification should only be done once.

**_1. successful/failed transaction_**

The flow related to FMS in forementioned process is demonstrated below:

| No. of step | description | API used|
|:------------|:------------|:----------------------|
| 1           | complete a transaction                     | n.a. (implemented by application server )  |
| 2           | notify FMS of a successfully/unsuccessfully paid order    |    /payment/webhook     |

In the event of the user cancelling the order or the transaction has error, it is suggested that application server waits until it gets the final transaction result within the payment time limit, before notifying FMS. The final result could indicate a succssful or a failed transaction. _If the final result still indicates a failed transation, notify FMS, then the pre-ordered profile will be released, and a new order should start from pre-order again._

**_2. time out_**

FMS has a timeout limit of **`60` minutes**, therefore if a notification is received after the time limit, error code will be returned, the pre-ordered profile will be released, and a new order should start from pre-order again. It is advised that application server sends the successful transaction notification without the time limit to avoid refund. 

| No. of step | description | API used|
|:------------|:------------|:----------------------|
| 1           | complete a transaction                     | n.a. (payment implemented by application server )  |
| 2           | notify FMS of a successful transaction `payment_intent.payment_succeed` after 10 minutes      |    /payment/webhook     |
| 3           | return by FMS, error code: `6006`          |  |
| 4           | submit a new order                         | /pacakge/preOrderPackage |


---

[back to top](/fms-api/flow/#flow)

---
[back to **general**](/fms-api/general){: .btn .btn-green .mr-4}            [next to **api**](/fms-api/apis/){: .btn .btn-purple }