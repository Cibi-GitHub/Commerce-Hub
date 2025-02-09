---
tags: [carat, commerce-hub, apple-pay, wallet, apple-pay-inapp-integration]
---

# Apple Pay: In-App Integration

#### Apple Pay on the App

## Step 1: Configure Apple Pay in App

Configure Apple developer account with merchant information to accept [Apple Pay in the App](https://help.apple.com/developer-account/#/devb2e62b839). This includes creating a merchant identifier, enabling Apple Pay in App and creating a processing certificate.

- When using *ApplePay*, the merchant will utilize the certificate generated by Commerce Hub. Please contact our Account Representative in order to get the certificate.
- When using *WalletDecrypted*, the merchant will utilize their own certificate.


---

## Step 2: Set-up Project in Xcode

A merchant will need to create a project in Xcode to start supporting Apple Pay in their app. Refer to Apple's website on how to [create the project in Xcode](https://developer.apple.com/documentation/xcode/creating_an_xcode_project_for_an_app) and [enable Apple Pay in Xcode](https://help.apple.com/xcode/mac/9.3/#/deva43983eb7?sub=dev44ce8ef13).

---

## Step 3: Submit a Payment Request

The merchant can submit a payment request to Apple to verify if apple pay is supported and to receive the encrypted wallet data. Refer to Apple Pay's [Creating Payment Request](https://developer.apple.com/library/archive/ApplePay_Guide/CreateRequest.html#//apple_ref/doc/uid/TP40014764-CH3-SW2) for more detail.


## Step 4: Submit a Charge Request

Option 1 - Encrypted Data (wallet encrypted data using apple encryption, commerce hub will decrypt)
Option 2 - Decrypted Wallet (Merchant using their own certificate and they decrypt themselves and send us card data)

<!--
type: tab
title: ApplePay
-->

##### Example of a Charge Payload Request.
```json
{
  "amount": {
    "total": "12.04",
    "currency": "USD"
  },
  "source": {
    "sourceType": "ApplePay",
    "data": "hbreWcQg980mUoUCfuCoripnHO210lvtizOFLV6PTw1DjooSwik778bH....",
    "header": {
      "applicationDataHash": "94ee059335e587e501cc4bf90613e0814f00a7b08bc7c648fd865a2af6a22cc2",
      "ephemeralPublicKey": "MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEvR....",
      "publicKeyHash": "KRsyW0NauLpN8OwKr+yeu4jl6APbgW05/TYo5eGW0bQ=",
      "transactionId": "31323334353637"
    },
    "signature": "MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgEFADCABgkqhki.....",
    "version": "EC_v1",
    "applicationData": "VEVTVA==",
    "merchantId": "merchant.com.fapi.tcoe.applepay",
    "merchantPrivateKey": "MHcCAQEE234234234opsmasdsalsamdsad/asdsad/asdasd/....."
  }
  "transactionDetails": {
    "captureFlag": true,
    "createToken": true,
    "tokenProvider": "RSA"
  }
}

```

<!--
type: tab
title: DecryptedWallet
-->

Add payload here (PaymentCard) add extra data like cryptogram and stuff

<!--
type: tab
title: Response
-->

##### Example of a Charge (201: Created) Response.

<!-- theme: info -->
> See [Error Responses](?path=docs/Resources/Guides/Response-Codes/HTTP.md) for additional examples.
```json
{
  "gatewayResponse": {
    "orderId": "R-3b83fca8-2f9c-4364-86ae-12c91f1fcf16",
    "transactionType": "charge",
    "transactionState": "authorized",
    "transactionOrigin": "ecom"
  },
  "transactionProcessingDetails": {
    "transactionDate": "2021-04-16",
    "transactionTime": "2021-04-16T16:06:05Z",
    "apiTraceId": "rrt-0bd552c12342d3448-b-ea-1142-12938318-7",
    "clientRequestId": "30dd879c-ee2f-11db-8314-0800200c9a66",
    "transactionId": "838916029301"
  },
  "source": "ApplePay",
  "tokenData": "1234123412340019",
  "PARId": "string",
  "declineDuplicates": false,
  "tokenSource": "string",
  "paymentReceipt": {
    "approvedAmount": {
      "total": "1.00",
      "currency": "USD"
    },
    "processorResponseDetails": null,
    "approvalStatus": "APPROVED",
    "approvalCode": "OK7118",
    "referenceNumber": "845366457890-TODO",
    "schemeTransactionID": "019078743804756",
    "processor": "fiserv",
    "responseCode": "00",
    "responseMessage": "APPROVAL",
    "hostResponseCode": "54022",
    "hostResponseMessage": "Approved",
    "localTimestamp": "2021-04-16T16:06:05Z",
    "bankAssociationDetails": {
      "associationResponseCode": "000",
      "transactionTimestamp": "2021-04-16T16:06:05Z",
      "transactionReferenceInformation": null,
    }
  }
}
```
<!-- type: tab-end -->

---

## See Also

- [API Explorer](../api/?type=post&path=/payments/v1/charges)
- [Apple Pay Web Integration RESTful API](?path=docs/Online-Mobile-Digital/Wallets-AltPayments/Apple-Pay/Apple-Pay-Web-REST.md)
- [Apple Pay Web Integration Hosted Page](?path=docs/Online-Mobile-Digital/Wallets-AltPayments/Apple-Pay/Apple-Pay-Web-HPP.md)
- [Charges](?path=docs/Resources/API-Documents/Payments/Charges.md)
- [Google Pay](?path=docs/Online-Mobile-Digital/Wallets-AltPayments/Google-Pay/Google-Pay.md)

---
