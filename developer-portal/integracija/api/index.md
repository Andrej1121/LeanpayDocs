## Leanpay API

Leanpay API allowing merchants to easy integrate new payment option with installments.

## Connection to the Leanpay API

Connecting to the Leanpay API requires adding Leanpay as a payment method on your website’s checkout or payment page. When your customer selects Leanpay, you should ensure that they are redirected to the Leanpay Checkout page. An example of an HTML form is shown in section Checkout Page. Before redirecting you will need to submit information about the payment, such as your vendor id, amount to be paid and several other fields.

## Leanpay API environments

\||Demo|  <https://lapp.leanpay.si>
\|Production|  <https://app.leanpay.si>
\


## Payment Flow

![](https://storage.googleapis.com/stoplight-resources/API-integration/payment-diagram.png)

When the customer is ready to pay for goods or services on your website, they select the Leanpay payment option on your website.

You request a token by passing payment details (e.g., vendor id, vendor transaction id, amount) to the Leanpay Checkout.

Leanpay returns the generated token.

- You redirect the customer to the Leanpay Checkout and include the token in the submitted form. Leanpay displays the relevant transaction page.

- The customer enters their payment information (term, grace) and confirms the transaction.

- Leanpay platform approves or rejects the transaction.

- We display the confirmation page, containing the payment result, on the Leanpay Checkout.

- Leanpay provides you with an asynchronous notification to your API URL confirming the transaction details and status.

- The customer is then automatically returned to the relevant page on your website.

## How to Create Vendor Account

Please see [Registrirajte se v Leanpay-Office DEMO okolje](https://leanpay.docs.stoplight.io/testiranje_integracije/registracija_v_leanpay_demo)

## Integration Steps

![](https://storage.googleapis.com/stoplight-resources/API-integration/integration-steps.png)

Leanpay platform uses REST API style. Integration with Leanpay platform contains only two HTTP requests:

1. [Request token for checkout page](https://docs.leanpay.si/api-integracija/API/standard/requesttoken)

![](https://storage.googleapis.com/stoplight-resources/Images/2020-12-16%2015_54_55-Postman.png)

2. [Redirect customer to checkout page](https://docs.leanpay.si/api-integracija/API/standard/checkoutpage)

![](https://storage.googleapis.com/stoplight-resources/Images/2020-12-16%2015_56_10-Leanpay%20-%20Work%20-%20Microsoft%E2%80%8B%20Edge.png)

First HTTP request must be performed between merchant’s server and Leanpay platform.

After token has been obtained, then merchant’s web app redirects user to Leanpay checkout page with token enclosed as HTML form parameter.

## CHECKOUT PAGE - POST /vendor/checkout

After the token has been received, merchant redirects customer to Leanpay checkout page. Redirecting should be performed with submitting to HTML form.

### API guide can be found in submenu [API - Standard - Customer Check-out](https://docs.leanpay.si/integracija_z_leanpay/api-integracija/API/standard/checkoutpage)

**NOTE**

You can also use a light box or iframe to present Leanpay Checkout page.

## Status Response

When the payment process is complete Leanpay sends the details of the transaction to the API URL that you provided during the vendor account registration process or on your vendor account. This is done with a standard HTTP POST request. The Leanpay server continues to post the status until a response of HTTP OK (200) is received from your server or the number of posts exceeds 10. Your platforom should expose REST web service for receiving transaction status response form Leanpay platform. REST web service for status response is described below.

|Status|Description|Min Status Delivery Time|Max Status Delivery Time|AVG Status Delivery Time|
\|---|---|---|---|---|---|---|
|SUCCESS|Successfull transaction|0.01 hours|96 hours|3 hours|
|CANCELED|Customer canceled the transaction by closing application window|0.01 hours|2 hours|0.5 hours|
|EXPIRED|Customer didn't finish application in 2 hours after starting application or was redirected to /vendor/checkout|2 hours|2 hours|2 hours|
|FAILED|Customers application was rejected or failed|0.01 hours|96 hours|1 hours|

**IMPLEMENTATION RECOMMENDATION**

For any other status than "SUCCESS" received you can offer the client other payment method or cancel the order to release stock of the order.

**NOTE**

If you did not provide your API URL, this operaton will not be performed by Leanpay platform.

You can set this parameter on [Vendor application](https://lvendor.leanpay.si/#/dashboard/company), section Company > Development > API URL

### Status response REST service specification

```
POST https://yourdomain.com/some/arbitrary/url/
Accept: application/json
Content-Type: applic
```

### Request – sent by Leanpay platform

API secret for calculating MD5 is "secret"

```
{
	"leanPayTransactionId":"2449",
	"vendorTransactionId":"test-ignore-1607591207867",
	"amount":300.00,
	"status":"SUCCESS",
	"md5Signature":"f6913090a21fdd20cdfafaacd2ca0179"
}

{
	"leanPayTransactionId":null,
	"vendorTransactionId":"test-ignore-1607955546145",
	"amount":150.00,
	"status":"CANCELED",
	"md5Signature":"50d4eb9fd0caec6f85b4f59733ea4cc5"
}

{
	"leanPayTransactionId":null,
	"vendorTransactionId":"test-ignore-1608101524391",
	"amount":150.00,"status":"EXPIRED",
	"md5Signature":"4f2962a260e13001546793a03c9acbc3"
}

{
	"leanPayTransactionId":null,
	"vendorTransactionId":"test-ignore-1606670599934",
	"amount":150.00,"status":"FAILED",
	"md5Signature":"d5747f5097928dd7ec5606175e53b8b7"
}
```

### Response – sent by your platform

Your status REST web service should respond only with HTTP status 200 with no body.

## Validating Status Response

We recommend that you validate the transaction details in the status response. This can be done as follows:

1. Create a pending transaction or order for a fixed amount on your website.
2. Redirect the customer to the Leanpay Checkout, where they complete the transaction.
3. Leanpay will post the transaction confirmation to your API URL. This will include the ‘amount’ parameter.
4. Your website should validate the parameters received by calculating the md5 signature (see section MD5 Signature). If successful, it should compare the value in the confirmation post (amount parameter) to the one from the pending transaction or order on your website. You can also compare other parameters such as ‘vendorTransactionId’.
5. Once you have validated the transaction data you can process the transaction, for example, by dispatching the goods ordered.

## MD5 Signature

A text field called md5Signature is included in the JSON submitted to your server API URL. The value of this field is a 128-bit message digest, expressed as a string of thirty-two hexadecimal digits in LOWERCASE. The md5Signature is constructed by performing an MD5 calculation on a string built up by concatenating the fields returned to your statusUrl page.

This includes:

- leanPayTransactionId
- vendorTransactionId
- the MD5 value of the ASCII equivalent of the secret word assigned to your Leanpay account
- amount
- status

The purpose of the ‘md5Signature’ field is to ensure the integrity of the data posted back to your server. You should always compare the ‘md5Signature’ field’s value posted by Leanpay’s servers with the one you calculated. To calculate the md5 signature value, you need to take the values of the fields listed above in same order as they were posted back to you, concatenate them and perform a MD5 calculation on this string.

**Sample in JAVA on how to calculate MD5 signature**

```
package com.leanpay.core.test.example;
 
import org.springframework.util.DigestUtils;
 
import java.math.BigDecimal;
import java.security.NoSuchAlgorithmException;
import java.text.DecimalFormat;
 
public class Md5SignatureExample {
 
    public static void main(String[] args) throws NoSuchAlgorithmException {
 
        String leanPayTransactionId = "123456789";
        String vendorTransactionId = "987654321";
        String secret = "secret";
        BigDecimal amount = BigDecimal.valueOf(100);
        String status = "SUCCESS";
 
        String hash = generateSignature(leanPayTransactionId, vendorTransactionId, secret, amount, status);
 
        // 403d15c591f9b6db781936b003acb25e
        System.out.println(hash);
    }
 
    private static String generateSignature(String leanPayTransactionId, String vendorTransactionId, String secret,
            BigDecimal amount, String status) throws NoSuchAlgorithmException {
 
        StringBuilder sb = new StringBuilder();
 
        // LeanPay transaction ID.
        sb.append(leanPayTransactionId);
 
        // Vendor transaction ID.
        sb.append(vendorTransactionId);
 
        // 123456789987654321
        System.out.println(sb.toString());
 
        // Vendor API secret word - MD5 value.
        String secretMd5 = DigestUtils.md5DigestAsHex(secret.getBytes());
        sb.append(secretMd5);
 
        // 1234567899876543215ebe2294ecd0e0f08eab7690d2a6ee69
        System.out.println(sb.toString());
 
        // Amount.
        sb.append(formatTwoDecimals(amount));
 
        // 1234567899876543215ebe2294ecd0e0f08eab7690d2a6ee69100.00
        System.out.println(sb.toString());
 
        // Status.
        sb.append(status);
 
        // 1234567899876543215ebe2294ecd0e0f08eab7690d2a6ee69100.00SUCCESS
        System.out.println(sb.toString());
 
        return DigestUtils.md5DigestAsHex(sb.toString().getBytes());
    }
 
    private static String formatTwoDecimals(BigDecimal number) {
 
        return new DecimalFormat("0.00").format(number);
    }
}
```

## NOTES

Force amount to two decimal format.

If we posted back to you ‘status’ which IS NOT „SUCCESS“, then you should use „null“ value for ‘leanPayTransactionId’ field during MD5 signature calculation.

<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<!-- Add icon library -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
</head>
<body>
  <br><br>
  <div class="wrapper"><p>Potrebujete pomoč pri implementaciji ali imate vprašanje?</p>
  <a href="mailto:partner@leanpay.si?subject=Pomoč pri implementaciji" target="_blank" download>
 <button class="btn"><i class="fa fa-paper-plane"></i> Pišite nam</button></div>
</body>
</html>
