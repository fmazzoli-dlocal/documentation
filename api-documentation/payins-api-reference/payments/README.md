# Payments

This service allows you to create, modify or read payments. For more details on specific types of payments, you can look at the following pages:

* [Credit Card Payments](credit-card-payments/)
* [Cash \(Ticket\) Payments](cash-ticket-payments.md)
* [Bank Transfer Payments](bank-transfer-payments.md)

{% api-method method="post" host="https://api.dlocal.com" path="/payments" %}
{% api-method-summary %}
Create a Payment
{% endapi-method-summary %}

{% api-method-description %}
Creates a new payment using any of the available payment methods.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="amount" type="number" required=true %}
Transaction amount \(in the currency entered in the field `currency`\)
{% endapi-method-parameter %}

{% api-method-parameter name="currency" type="string" required=true %}
Three-letter ISO-4217 currency code, in uppercase.
{% endapi-method-parameter %}

{% api-method-parameter name="payment\_method\_id" type="string" required=false %}
Payment method code chosen to make the payment, or the keyword `CARD`  
**Required for** `DIRECT` **payment method flow.**
{% endapi-method-parameter %}

{% api-method-parameter name="payment\_method\_flow" type="string" required=true %}
Payment method flow, can be `DIRECT` or `REDIRECT`
{% endapi-method-parameter %}

{% api-method-parameter name="country" type="string" required=true %}
User's country code. ISO 3166-1 alpha-2 code.
{% endapi-method-parameter %}

{% api-method-parameter name="payer" type="object" required=true %}
Payer Object
{% endapi-method-parameter %}

{% api-method-parameter name="card" type="object" required=false %}
Card Object  
**Required only for** `CARD` **payment type.**
{% endapi-method-parameter %}

{% api-method-parameter name="direct\_debit" type="object" required=false %}
Direct Debit Object  
**Required only for** `DIRECT_DEBIT` **payment type.**
{% endapi-method-parameter %}

{% api-method-parameter name="order\_id" type="string" required=true %}
ID given by the merchant in their system.
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
Payment description.
{% endapi-method-parameter %}

{% api-method-parameter name="notification\_url" type="string" required=false %}
URL where dlocal will send notifications associated to changes to this payment.
{% endapi-method-parameter %}

{% api-method-parameter name="callback\_url" type="string" required=false %}
URL where dlocal does the final redirect.   
**Required only for `REDIRECT` payment method flow.**
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Example Response
{% endapi-method-response-example-description %}

```yaml
{
    "id": "PAY2323243343543",
    "amount": 120.00,
    "currency" : "USD",
    "country": "BR",
    "payment_method_id" : "CARD",
    "payment_method_type" : "CARD",
    "payment_method_flow" : "DIRECT",
    "card":{
        "card_id": "CV-e90078f7-e027-4ce4-84cb-534c877be33c",
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "last4": "1111",
        "brand": "VI"
    },
    "created_date" : "2018-02-15T15:14:52-00:00",
    "approved_date" : "2018-02-15T15:14:52-00:00",
    "status" : "PAID",
    "status_code" : "200",
    "status_detail" : "The payment was paid.",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### The Payer Object

{% tabs %}
{% tab title="Payer Object" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `name` | String | User's full name. **Required.** |
| `email` | String | User’s email address. **Required.** |
| `birth_date` | String | User’s birthdate \(DD-MM-YYYY\). Optional. |
| `phone` | String | User’s phone. Optional. |
| `document` | String | User’s personal identification number. [Click here for more details.](../country-reference.md#documents) **Required**. |
| `user_reference` | String | Unique user id at the merchant side. Optional. |
| `address` | [Address Object ](./#the-address-object) | User’s address. **Only required in India.** |
{% endtab %}

{% tab title="Example Payer Object" %}
```yaml
{
"name" : "Thiago Gabriel",
"email" : "thiago@example.com",
"document" : "53033315550",
"user_reference": "12345",
"address": {
    "state"  : "Rio de Janeiro",
    "city" : "Volta Redonda",
    "zip_code" : "27275-595",
    "street" : "Servidão B-1",
    "number" : "1106"
}
}
```
{% endtab %}
{% endtabs %}

#### The Address Object

{% tabs %}
{% tab title="Address Object" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `state` | String | User's address state. Optional. |
| `city` | String | User’s address city. **Only required in India.** |
| `zip_code` | String | User’s address zip\_code. Optional. |
| `street` | String | User’s address street. **Only required in India.** |
| `number` | String | User’s address number. **Only required in India.** |
{% endtab %}

{% tab title="Example Address Object" %}
```yaml
{
"state"  : "Rio de Janeiro",
"city" : "Volta Redonda",
"zip_code" : "27275-595",
"street" : "Servidão B-1",
"number" : "1106"
}
```
{% endtab %}
{% endtabs %}

#### The Card Object

For credit card payments you can use the card information only if you business is [Full PCI DSS compliant](../../../solutions/payins.md#pci-compliance). Otherwise you need to collect the card information using [Smart Fields](../../../products/smart-fields/). For recurring payments, first [save the card](../saving-cards.md#create-a-card), and then use the `card_id` to charge the card.

{% hint style="warning" %}
**Important**: If you are making a payment **with credit card information**, you need to use the following endpoint instead:  
https://api.dlocal.com/secure\_payments

Card payments with a `card_id` or `token` should use the endpoint: https://api.dlocal.com/payments
{% endhint %}

{% tabs %}
{% tab title="Card Object" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `holder_name` | String | Cardholder's full name. **Required if** `token` **or** `card_id` **not present** |
| `expiration_month` | Integer | Two digit number representing the card's expiration month. **Required if** `token` **or** `card_id` **not present** |
| `expiration_year` | Integer | Four digit number representing the card's expiration year. **Required if** `token` **or** `card_id` **not present** |
| `number` | String | The card number, as a string without any separators.  **Required if**`encrypted_data` **,**`token` **or** `card_id` **not present** |
| `cvv` | String | Credit card verification value. Optional. **Required for India.** |
| `encrypted_data` | String | [JWE](https://tools.ietf.org/html/rfc7516) encrypted params. Optional. |
| `token` | String | Temporary credit card token securely created using [Smart Fields](../../../products/smart-fields/). Optional. |
| `cvv_token` | String | Temporary CVV token securely created using the CVV-only Smart Field. |
| `card_id` | String | Credit card id returned by the [Create a Card ](../saving-cards.md#create-a-card)call. Optional. |
| `installments` | String | Number of installments. Default 1. Optional. |
| `installments_id` | String | Installments id of a installments plan. Optional. |
| `descriptor` | String | Dynamic Descriptor.  Optional. |
| `capture` | Boolean | Whether or not to immediately capture the charge. When false, the charge issues an authorization, and will need to be captured later. Default `TRUE`. Optional. |
{% endtab %}

{% tab title="Example Card Object" %}
#### Example with raw credit card information:

```yaml
{
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "number": "4111111111111111",
        "cvv": "123"
 }
```

#### Example with Smart Fields `token`:

```text
{
    "token":"CV-124c18a5-874d-4982-89d7-b9c256e647b5"
}
```

#### Example with `card_id` from Create a Card method:

```text
{    
    "card_id":"CV-hgv23jh4g-n23n-kj3k-bkhb3-kj3hj3gjh3k3"
}
```
{% endtab %}
{% endtabs %}

#### The Direct Debit Object

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `holder_name` | String | Name of the owner of the bank account. **Required.** |
| `email` | String | Email of the owner of the bank account. **Required.** |
| `document` | String | Document of the owner of the bank account. **Required.** |
| `cbu` | String | CBU of the owner of the bank account.. **Required only for Argentina.** |

### Example Request

{% tabs %}
{% tab title="Payment with Credit Card Information " %}
The following example applies for credit card payments using the plain credit card information \(**only for Full PCI DSS merchants**\). To make payments using encrypted card information, simply **replace** the `number`and `cvv`parameters with [`encrypted_data`](../security.md#sensitive-data-encryption).

#### Example Request

```bash
curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Content-Type: application/json' \
    -H 'X-Version: 2.1' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/secure_payments
```

#### Example Request Body

```yaml
{
    "amount": 120.00,
    "currency" : "USD",
    "country": "BR",
    "payment_method_id" : "CARD",
    "payment_method_flow" : "DIRECT",
    "payer":{
        "name" : "Thiago Gabriel",
        "email" : "thiago@example.com",
        "document" : "53033315550",
        "user_reference": "12345",
        "address": {
            "state"  : "Rio de Janeiro",
            "city" : "Volta Redonda",
            "zip_code" : "27275-595",
            "street" : "Servidao B-1",
            "number" : "1106"
        }
    },
    "card":{
        "holder_name" : "Thiago Gabriel",
        "number" : "4111111111111111",
        "cvv" : "123",
        "expiration_month" : 10,
        "expiration_year" : 2040
    },
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}

{% tab title="Payment with Credit Card Token" %}
The following example applies for credit card payments using a Smart Fields `token`. To make a payment with a `card_id`obtained from the [Create a Card](../saving-cards.md#create-a-card) method, simply **replace** the `token`parameter with `card_id`.

#### Example Request

```bash
curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/payments
```

#### Example Request Body

```yaml
{
    "amount": 120.00,
    "currency" : "USD",
    "country": "BR",
    "payment_method_id" : "CARD",
    "payment_method_flow" : "DIRECT",
    "payer":{
        "name" : "Thiago Gabriel",
        "email" : "thiago@example.com",
        "document" : "53033315550",
        "user_reference": "12345",
        "address": {
            "state"  : "Rio de Janeiro",
            "city" : "Volta Redonda",
            "zip_code" : "27275-595",
            "street" : "Servidao B-1",
            "number" : "1106"
        }
    },
    "card":{
        "token": "CV-124c18a5-874d-4982-89d7-b9c256e647b5"
    },
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}

{% api-method method="get" host=" https://api.dlocal.com/payments/" path="{payment\_id}" %}
{% api-method-summary %}
Retrieve a Payment
{% endapi-method-summary %}

{% api-method-description %}
Retrieve information about an existing payment.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="payment\_id" type="string" required=true %}
The payment id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "id" : "D-4-16112abb-b2c6-4799-86db-497c6bd321ac",
   "amount" : 120.00,
   "currency" : "USD",
   "payment_method_id" : "CARD",
   "payment_method_type" : "CARD",
   "payment_method_flow" : "DIRECT",
   "country" : "BR",
   "card" : {
      "holder_name" : "Thiago Gabriel",
      "expiration_month" : 10,
      "expiration_year" : 2040,
      "brand" : "VI",
      "last4" : "1111",
      "card_id" : "CV-a9b713b7-3064-4a59-8cd7-bd940326fa43"
   },
   "created_date" : "2018-07-012T21:42:27.000+0000",
   "approved_date" : "2018-07-012T21:42:28.000+0000",
   "status" : "AUTHORIZED",
   "status_detail" : "The payment was authorized",
   "status_code" : "600",
   "order_id" : "657434343",
   "notification_url" : "http://merchant.com/notifications",
   "refunds" : []
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Example Request

```bash
$ curl \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'X-Version: 2.1' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/payments/PAY4334346343
```

{% api-method method="get" host="https://api.dlocal.com/payments/" path="{payment\_id}/status" %}
{% api-method-summary %}
Retrieve a Payment Status
{% endapi-method-summary %}

{% api-method-description %}
Retrieve information about the status of an existing payment.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="payment\_id" type="string" required=true %}
The payment id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Example Response
{% endapi-method-response-example-description %}

```yaml
{
    "id": "PAY4334346343",
    "status" : "PAID",
    "status_detail" : "The payment was paid.",
    "status_code" : "200",
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Example Request

```bash
$ curl \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'X-Version: 2.1' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/payments/PAY4334346343/status
```

## Payment Status Codes

| **Status** | **Status code** | **Description** |
| :--- | :--- | :--- |
| `PENDING` | 100 | The payment is pending. |
| `PAID` | 200 | The payment was paid. |
| `REJECTED` | 300 | The payment was rejected. |
| `CANCELLED` | 400 | The payment was cancelled. |
| `EXPIRED` | 500 | The payment was expired. |
| `AUTHORIZED` | 600 | The payment was authorized. |

### Rejection Status

| **Status** | **Status code** | **Description** |
| :--- | :--- | :--- |
| `REJECTED` | 300 | The payment was rejected. |
| `REJECTED` | 301 | Rejected by bank. |
| `REJECTED` | 302 | Insufficient amount. |
| `REJECTED` | 303 | Card blacklisted. |
| `REJECTED` | 304 | Score validation. |
| `REJECTED` | 305 | Max attempts reached. |
| `REJECTED` | 306 | Call bank for authorize. |
| `REJECTED` | 307 | Duplicated payment. |
| `REJECTED` | 308 | Credit card disabled. |
| `REJECTED` | 309 | Card expired. |
| `REJECTED` | 310 | Card reported lost. |
| `REJECTED` | 311 | Card requested by the bank. |
| `REJECTED` | 312 | Card restricted by the bank. |
| `REJECTED` | 313 | Card reported stolen. |
| `REJECTED` | 314 | Invalid card number. |
| `REJECTED` | 315 | Invalid security code. |
| `REJECTED` | 316 | Unsupported operation. |
| `REJECTED` | 317 | Rejected due to high risk. |
| `REJECTED` | 318 | Invalid transaction. |
| `REJECTED` | 319 | Amount exceeded. |

### Pending Status

| **Status** | **Status code** | **Description** |
| :--- | :--- | :--- |
| `PENDING` | 100 | The payment is pending. |
| `PENDING` | 101 | The payment is pending 3D Secure authentication. |

### Errors

Below you can find an example of a **Credit Card** payment. For more examples [visit this page](credit-card-payments/).

For examples of **Cash \(ticket\)** payments, [visit this page](cash-ticket-payments.md).

For examples of **Bank Transfer** payments, [visit this page](bank-transfer-payments.md).

All the errors are returned with appropriate HTTP status code, 4XX or 5XX. The format of all errors is:

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `code` | Integer | Error code. |
| `message` | String | Human readable message. |
| `param` | String | In case one parameter is wrong. |

**Example error**

```yaml
{
    "code": 5005,
    "message": "User unauthorized due to cadastral situation"
}
```

#### Http Errors <a id="http-errors"></a>

| **HTTP Status Code** | **Error Code** | **Error Detail** |
| :--- | :--- | :--- |
| `403 Forbidden` | 3001 | Invalid Credentials. |
|  | 3002 | Unregistered IP address. |
|  | 3003 | Merchant has no authorization to use this API. |
| `404 Not Found` | 4000 | Payment not found. |
| `400 Bad Request` | 5000 | Invalid request. |
|  | 5001 | Invalid parameter: \[parameter\_name\] |
|  | 5002 | Invalid transaction status. |
|  | 5003 | Country not supported. |
|  | 5004 | Currency not allowed for this country. |
|  | 5005 | User unauthorized due to cadastral situation. |
|  | 5006 | User limit exceeded. |
|  | 5007 | Amount exceeded. |
|  | 5008 | Token not found or inactive. |
|  | 5009 | Order id is duplicated. |
|  | 5010 | Request timeout. |
|  | 5013 | Unsupported operation. |
|  | 5014 | User blacklisted. |
|  | 5016 | Amount too low. |
|  | 5017 | Invalid API Version. |
|  | 5018 | Chargeback in place for this transaction. |
| `429 Too many requests` | 6000 | Too many requests to the API. |
| `500 Internal Server Error` | 7000 | The input is correct, but dLocal fails to process the payment. Rare case. |

## Notifications

Notifications will be sent in every change of status of a payment to the notification URL specified by the merchant. This URL is taken from the `notification_url` field of the payment, if it differs from the one specified in the merchant panel. The body of the request will always be the payment object.

{% hint style="info" %}
Until dLocal receives a 200 status code confirmation on these notifications, it will retry every 10 minutes for 30 days.
{% endhint %}

#### Example Notification POST

POST: _{payment.notification\_url}_

```yaml
{
    "id": "PAY4334346343",
    "amount": 150.00,
    "currency" : "ARS",
    "country": "AR",
    "payment_method_id" : "GL",
    "payment_method_type" : "BANK_TRANSFER",
    "payment_method_flow" : "DIRECT",
    "payer":{
        "name" : "Juan Gomez",
        "email" : "juan@example.com",
        "document" : "58473832",
        "address": {
            "country" : "AR",
            "state"  : "Buenos Aires",
            "city" : "Buenos Aires",
            "zip_code" : "272235-595",
            "street" : "Gobernador",
            "number" : "5433"
        }
    },
    "bank_transfer":{
        "type": "CURRENT_ACCOUNT",
        "name": "Banco de Galicia",
        "code": "GL",
        "beneficiary": "ARS CAPITAL SA",
        "document": "4234234243",
        "reference": "43423245",
        "amount_to_transfer": 150.01
    },
    "created_date" : "2018-02-15T15:14:52-00:00",
    "status" : "PENDING",
    "status_code" : "100"
    "status_detail" : "The payment is pending."
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```

### Signature of Notifications

An HMAC signature is calculated using a request's key-value pairs and a secret key, which is known only to you and dLocal. By verifying this signature, you'll confirm that the notification was not modified during transmission.

dLocal will be signing each POST notification using the same method described on the[ **Security section our the documentation**](../security.md) ****\(SHA256 HMAC hash function\)**.**

Simply take the `Authorization` HTTP header from the notification, and compare it with the one generated by you using your `X-Login` and `secretKey`, and the `X-Date`and Request body of the notification received. If the signature generated by you matched the one received on the `Authorization` HTTP header, then it is safe to assume that this is a valid message from dLocal.

