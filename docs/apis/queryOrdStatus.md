---
layout: default
title: queryOrdStatus
parent: apis
nav_order: 7
---

# queryOrdStatusAndEmail

After transanction is complete, backend service is required to call this API and loop request its response until the correct result (`non zero value`) is returned, please refer to [`package/queryOrdStatusAndEmail`](http://47.56.82.232:49090/swagger-ui.html#/package-controller/queryOrderStatusAndEmailUsingPOST) for api details

## request

```json

{
  "orderId" : <orderid>
}

```

## parameters

- `orderId` is the order that a transanction is to be completed


## Code example

```swift
NetProvider.shared.requestDataWithTargetJSON(target: NetPlan.orderStatus(orderId: orderId),isAutoDismissHUD: false, successClosure: { [weak self] (resJson) in
            let planOrder = Mapper<PlanOrderModel>().map(JSON: resJson.object as! [String : Any])
            self?.orderInfo = planOrder
            printLog(resJson)
            if planOrder?.orderPayStatus == 1 { //transaction is complete
                SVProgressHUD.dismiss()
              callback(.success)
            } else if planOrder?.orderPayStatus == 2 { //transaction is not successful
                SVProgressHUD.dismiss()
                SVProgressHUD.showInfo(withStatus: localizeStr("payOrderFailed"))
              callback(.fail)
            } else if planOrder?.orderPayStatus == 3 { //order is cancelled
                SVProgressHUD.dismiss()
                SVProgressHUD.showInfo(withStatus: localizeStr("payOrderCanceled"))
              callback(.cancel)
            } else if planOrder?.orderPayStatus == 0 {
              //wating for transaction, request again after 2s.
          }
        }) { (errorMsg) in
          callback(.error)
            SVProgressHUD.dismiss()
            SVProgressHUD.showInfo(withStatus: errorMsg)
        }


``` 

## Response

QR code will be given in the response of this API when `stataus == 1`, it can be displayed to the end user right after the transaction is successful. The QR code is also sent to the user regsitered email.

```json
{
  "orderPayStatus": 1,
  "qrCode" : <string>

}

```

---
