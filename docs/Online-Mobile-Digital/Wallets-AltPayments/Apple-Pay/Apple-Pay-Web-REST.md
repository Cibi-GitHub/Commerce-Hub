---
tags: [carat, commerce-hub, apple-pay, wallet, apple-pay-web-integration]
---

# Apple Pay on the Web: RESTful API Integration

## Step 1: Configure Apple Pay on the Web

Configure Apple developer account with merchant information to accept [Apple Pay on the web](https://help.apple.com/developer-account/#/dev1731126fb). This includes creating a merchant identifier, creating a processing certificate, registering the merchant and creating a merchant identity certificate.

- When using *ApplePay*, the merchant will utilize the certificate generated by Commerce Hub. Please contact our Account Representative in order to get the certificate.
- When using *DecryptedWallet*, the merchant will utilize their own certificate.

---

## Step 2: Support Apple Pay on the Web

The merchant can start supporting Apple Pay on their website by using the Commerce Hub's [RESTful API](docs/Resources/API-Documents/Use-Our-APIs.md) with [Apple Pay's JS API Framework](https://developer.apple.com/documentation/apple_pay_on_the_web/apple_pay_js_api).

---

## Step 3: Presenting the Payment Sheet

The merchant can enhance the purchase experience from their website by creating a streamlined checkout process and presenting a customized Apple Pay payment sheet that allows customers to promptly authorize a payment and complete their transaction. Refer to Apple's website on how to customize the [payment sheet](https://developer.apple.com/design/human-interface-guidelines/apple-pay/overview/checkout-and-payment/#customize-the-payment-sheet).

---

## Step 4: Submit a Payment Request

<!--
type: tab
title: Request
-->

##### Example of a Charge Payload Request.
```json
{
   "amount":{
      "total":"12.04",
      "currency":"USD"
   },
   "source":{
      "sourceType":"ApplePay",
      "data":"hbreWcQg980mUoUCfuCoripnHO210lvtizOFLV6PTw1DjooSwik778bH....",
      "header":{
        "applicationDataHash":"94ee059335e587e501cc4bf90613e0814f00a7b08bc7c648fd865a2af6a22cc2",
        "ephemeralPublicKey":"MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEvR....",
        "publicKeyHash":"KRsyW0NauLpN8OwKr+yeu4jl6APbgW05/TYo5eGW0bQ=",
        "transactionId":"31323334353637"
      },
      "signature":"MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgEFADCABgkqhki.....",
      "version":"EC_v1",
      "applicationData":"VEVTVA==",
      "merchantId":"merchant.com.fapi.tcoe.applepay",
      "merchantPrivateKey":"MHcCAQEE234234234opsmasdsalsamdsad/asdsad/asdasd/....."
   },
   "transactionDetails":{
      "captureFlag":true,
      "createToken":true,
      "tokenProvider":"RSA"
   }
   "transactionInteraction":{
      "eciIndicator": "SECURE_ECOM",
   }
}

```

<!--
type: tab
title: Response
-->

##### Example of a Charge (201: Created) Response.

<!-- theme: info -->
> See [Error Responses](?path=docs/Resources/Guides/Response-Codes/HTTP.md) for additional examples.
```json
{
   "gatewayResponse":{
      "orderId":"R-3b83fca8-2f9c-4364-86ae-12c91f1fcf16",
      "transactionType":"charge",
      "transactionState":"authorized",
      "transactionOrigin":"ecom"
   },
   "transactionProcessingDetails":{
      "transactionDate":"2021-04-16",
      "transactionTime":"2021-04-16T16:06:05Z",
      "apiTraceId":"rrt-0bd552c12342d3448-b-ea-1142-12938318-7",
      "clientRequestId":"30dd879c-ee2f-11db-8314-0800200c9a66",
      "transactionId":"838916029301"
   },
   "source":"ApplePay",
   "paymentToken":{
      "tokenData":"1234123412340019",
      "PARId":"string",
      "declineDuplicates":false,
      "tokenSource":"RSA"
   },
   "paymentReceipt":{
      "approvedAmount":{
         "total":"1.00",
         "currency":"USD"
      },
      "processorResponseDetails":null,
      "approvalStatus":"APPROVED",
      "approvalCode":"OK7118",
      "referenceNumber":"845366457890-TODO",
      "schemeTransactionID":"019078743804756",
      "processor":"fiserv",
      "responseCode":"00",
      "responseMessage":"APPROVAL",
      "hostResponseCode":"54022",
      "hostResponseMessage":"Approved",
      "localTimestamp":"2021-04-16T16:06:05Z",
      "bankAssociationDetails":{
         "associationResponseCode":"000",
         "transactionTimestamp":"2021-04-16T16:06:05Z",
         "transactionReferenceInformation":null
      }
   }
}
```

<!-- type: tab-end -->

---

## See Also

- [API Explorer](../api/?type=post&path=/payments/v1/charges)
- [Apple Pay App Integration](?path=docs/Online-Mobile-Digital/Wallets-AltPayments/Apple-Pay/Apple-Pay.md)
- [Charges](?path=docs/Resources/API-Documents/Payments/Charges.md)
- [Google Pay](?path=docs/Online-Mobile-Digital/Wallets-AltPayments/Google-Pay/Google-Pay.md)

---