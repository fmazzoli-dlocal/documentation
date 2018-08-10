# Payments

This service allows you to create, modify or read payments.

## The Payment Object

{% tabs %}
{% tab title="Payment Object" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | String | Id of payment |
| `amount` | Positive Float | Transaction amount \(in the currency entered in the field “currency”\). |
| `currency` | String | Three-letter [ISO currency code](https://www.iso.org/iso-4217-currency-codes.html), in uppercase. |
| `payment_method_id` | String | Payment method id of the payment method chosen. [See all payment method codes here.](payment-methods.md#payment-method-codes) |
| `payment_method_type` | String | Payment method type of the payment method chosen. Type of method can be `CARD` `BANK_TRANSFER` `DIRECT_DEBIT` `TICKET`. |
| `payment_method_flow` | String | Payment method flow of the payment method chosen, can be `DIRECT` or `REDIRECT`. |
| `country` | String | User’s country code. ISO 3166-1 alpha-2 codes. |
| `payer` | [Payer Object](payments.md#the-payer-object) | Identifies the payer |
| `card` | [Card Object](payments.md#the-card-object) | Credit card information \( only for CARD payment methods \). |
| `bank_transfer` | [Bank Transfer Object](payments.md#the-bank-transfer-object) | Bank transfer information \( only for BANK\_TRANSFER payment methods \). |
| `direct_debit` | [Direct Debit Object](payments.md#the-direct-debit-object) | Bank information for direct debit \( only for DIRECT\_DEBIT payment methods \). |
| `ticket` | [Ticket Object](payments.md#the-ticket-object) | Ticket information \( only for TICKET payment methods \). |
| `refunds` | [Refund Object](refunds.md#the-refund-object) | Payment's refunds of refund object. |
| `created_date` | Date\(ISO\_8601\) | Payment's creation date. |
| `approved_date` | Date\(ISO\_8601\) | Payment's approval date. |
| `status` | String | Payment status. [See all payment status.](payments.md#payment-status-codes) |
| `status_detail` | String | Payment status detail. |
| `status_code` | String | Status code.[ See all payment status codes.](payments.md#payment-status-codes) |
| `order_id` | String | ID given by the merchant in their system. |
| `description` | String | Payment description |
| `notification_url` | String | URL where dlocal will send notifications associated to changes in this payment. |
| `callback_url` | String | URL where dlocal does the final redirect \(only for bank transfers and tickets\). |
| `redirect_url` | String | URL where the merchant must redirect the user to complete the payment. |
{% endtab %}

{% tab title="Example Payment Object" %}
```yaml
{
    "id": "3436735432",
    "amount": 120.00,
    "currency" : "USD",
    "country": "BR",
    "payment_method_id" : "VI",
    "payment_method_type" : "CARD",
    "payment_method_flow" : "DIRECT",
    "payer":{
        "name" : "Thiago Gabriel",
        "email" : "thiago@example.com",
        "document" : "53033315550",
        "document_type" : "CPF",
        "user_reference": "12345",
        "address": {
            "state"  : "Rio de Janeiro",
            "city" : "Volta Redonda",
            "zip_code" : "27275-595",
            "street" : "Servidão B-1",
            "number" : "1106"
        }
    },
    "card":{
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "last4": "4544",
        "brand": "VI",
        "capture": true
    },
    "refunds": [],
    "created_date" : "2018-02-15T15:14:52-00:00",
    "approved_date" : "2018-02-15T15:14:52-00:00",
    "status" : "PENDING",
    "status_detail" : "The payment is pending.",
    "status_code" : "100",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}

## The Payer Object

{% tabs %}
{% tab title="Payer Object" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `name` | String | User's full name |
| `email` | String | User’s email address. |
| `birth_date` | String | User’s birthdate \(DD-MM-YYYY\). |
| `phone` | String | User’s phone. |
| `document` | String | User’s personal identification number: CPF or CNPJ for Brazil, DNI for Argentina and ID for other countries. |
| `document_type` | String | User’s document type. |
| `user_reference` | String | Unique user id at the merchant side. |
| `address` | [Address Object](payments.md#the-address-object) | User’s address. |
{% endtab %}

{% tab title="Example Payer Object" %}
```yaml
{
"name" : "Thiago Gabriel",
"email" : "thiago@example.com",
"document" : "53033315550",
"document_type" : "CPF",
"user_reference": "12345",
"address": {
    "country" : "BR",
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

## The Address Object

{% tabs %}
{% tab title="Address Object" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `state` | String | User's address state. |
| `city` | String | User’s address city. |
| `zip_code` | String | User’s address zip\_code. |
| `street` | String | User’s address street. |
| `number` | String | User’s address number. |
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

## The Card Object

{% tabs %}
{% tab title="Card Object" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `holder_name` | String | Cardholder's full name |
| `expiration_month` | Integer | Two digit number representing the card's expiration month. |
| `expiration_year` | Integer | Four digit number representing the card's expiration year. |
| `token` | String | Credit card token. |
| `number` | String | The card number, as a string without any separators. |
| `cvv` | String | Credit card verification value. |
| `encrypted_data` | String | [JWE](https://tools.ietf.org/html/rfc7516) encrypted params |
| `token` | String | Temporary credit card token securely created using [Smart Fields](../../products/smart-fields/). |
| `card_id` | String | Credit card if returned by the [Create a Card](saving-cards.md#create-a-card) call. |
| `brand` | String | Card brand code. |
| `installments` | String | Number of installments. |
| `installments_id` | String | Installments id of a [installments plan](installments.md#the-installment-plan-object). |
| `descriptor` | String | Dynamic Descriptor. |
| `last4` | String | The last 4 digits of the card. |
| `save` | String | Indicate if the card must be save for future payments, can be `YES`, `NO`, `ASK_USER` \( ask user is only for `REDIRECT` payment method flows \) |
| `capture` | Boolean | Whether or not to immediately capture the charge. When false, the charge issues an authorization, and will need to be captured later. |
{% endtab %}

{% tab title="Example Card Object" %}
```yaml
{
"token": "CV-e90078f7-e027-4ce4-84cb-534c877be33c",
"holder_name": "Thiago Gabriel",
"expiration_month": 10,
"expiration_year": 2040,
"last4": "1111",
"brand": "VI",
"capture": false
}
```
{% endtab %}
{% endtabs %}

## The Bank Transfer Object

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `type` | String | Bank account type |
| `name` | String | Bank name. |
| `code` | String | Bank code. |
| `beneficiary` | String | Beneficiary name. |
| `account` | String | Bank account number. |
| `document_type` | String | Beneficiary document type. |
| `document` | String | Beneficiary document number. |
| `amount_to_transfer` | Positive Float | Amount to transfer \(only for not referenced bank transfers\). |
| `reference` | String | Reference to make the bank transfer. |

## The Direct Debit Object

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `holder_name` | String | Name of the owner of the |
| `email` | String | Email of the owner of the bank account. |
| `document_type` | String | Document of the owner of the bank account. |
| `document` | String | Document of the owner of the bank account. |
| `cbu` | String | CBU of the owner of the bank account \(only for AR country\). |

## The Ticket Object

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `type` | String | Type of ticket, can be `REFERENCE_CODE`, or `BAR_CODE` |
| `format` | String | Ticket barcode format only for `BAR_CODE`, for example `CODE_128`. |
| `number` | String | Ticket number. |
| `expiration_date` | Date\(ISO-8601\) | The expiration date of the ticket. |

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
Three-letter ISO currency code, in uppercase.
{% endapi-method-parameter %}

{% api-method-parameter name="payment\_method\_id" type="string" required=false %}
Payment method code chosen to make the payment, or the keyword `CARD`
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
URL where dlocal does the final redirect \(only for bank transfers and tickets\)
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
    "payment_method_type" : "CARD",
    "payment_method_flow" : "DIRECT",
    "card":{
        "token": "CV-e90078f7-e027-4ce4-84cb-534c877be33c",
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "last4": "1111",
        "brand": "VI",
        "capture": false,
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
| `name` | String  | User's full name. **Required.** |
| `email` | String  | User’s email address. **Required.** |
| `birth_date` | String  | User’s birthdate \(DD-MM-YYYY\). Optional. |
| `phone` | String  | User’s phone. Optional. |
| `document` | String  | User’s personal identification number: CPF or CNPJ for Brazil, DNI for Argentina and ID for other countries. **Required**. |
| `document_type` | String  | User’s document type. Optional. |
| `user_reference` | String  | Unique user id at the merchant side. Optional. |
| `address` | [Address Object ](payments.md#the-address-object) | User’s address. Optional. |
{% endtab %}

{% tab title="Example Payer Object" %}
```yaml
{
"name" : "Thiago Gabriel",
"email" : "thiago@example.com",
"document" : "53033315550",
"document_type" : "CPF",
"user_reference": "12345",
"address": {
    "country" : "BR",
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
| `city` | String | User’s address city. Optional. |
| `zip_code` | String | User’s address zip\_code. Optional. |
| `street` | String | User’s address street. Optional. |
| `number` | String | User’s address number. Optional. |
{% endtab %}

{% tab title="Example Address Object" %}
```yaml
{
"country" : "BR",
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

For credit card payments you can use the card information only if you business is [Full PCI DSS compliant](../../solutions/payins.md#pci-compliance). Otherwise you need to collect the card information using [Smart Fields](../../products/smart-fields/). For recurring payments, first [save the card](saving-cards.md#create-a-card), and then use the `card_id` to charge the card.

{% tabs %}
{% tab title="Card Object" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `holder_name` | String | Cardholder's full name. **Required if** `token` **or** `card_id` **not present** |
| `expiration_month` | Integer | Two digit number representing the card's expiration month. **Required if** `token` **or** `card_id` **not present** |
| `expiration_year` | Integer | Four digit number representing the card's expiration year. **Required if** `token` **or** `card_id` **not present** |
| `number` | String | The card number, as a string without any separators.  **Required if**`encrypted_data` **,**`token` **or** `card_id` **not present** |
| `cvv` | String | Credit card verification value. **Required if**`encrypted_data` **,**`token` **or** `card_id` **not present** |
| `encrypted_data` | String | [JWE](https://tools.ietf.org/html/rfc7516) encrypted params. Optional. |
| `token` | String | Temporary credit card token securely created using [Smart Fields](../../products/smart-fields/). Optional. |
| `card_id` | String | Credit card id returned by the [Create a Card ](saving-cards.md#create-a-card)call. Optional. |
| `installments` | String | Number of installments. Default 1. Optional. |
| `installments_id` | String | Installments id of a installments plan. Optional. |
| `descriptor` | String | Dynamic Descriptor.  Optional. |
| `capture` | Boolean | Whether or not to immediately capture the charge. When false, the charge issues an authorization, and will need to be captured later. Default `TRUE`. Optional. |
{% endtab %}

{% tab title="Example Card Object" %}
```yaml
{
        "token": "CV-e90078f7-e027-4ce4-84cb-534c877be33c",
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "last4": "1111",
        "brand": "VI",
        "capture": false
    }
```
{% endtab %}
{% endtabs %}

#### The Direct Debit Object

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `holder_name` | String | Name of the owner of the bank account. **Required.** |
| `email` | String | Email of the owner of the bank account. **Required.** |
| `document_type` | String | Document of the owner of the bank account. **Required.** |
| `document` | String | Document of the owner of the bank account. **Required.** |
| `cbu` | String | CBU of the owner of the bank account \(**only for AR country**\). **Required.** |

### Example Request

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
    "payment_method_type" : "CARD",
    "payment_method_flow" : "DIRECT",
    "payer":{
        "name" : "Thiago Gabriel",
        "email" : "thiago@example.com",
        "document" : "53033315550",
        "document_type" : "CPF",
        "user_reference": "12345",
        "address": {
            "country" : "BR",
            "state"  : "Rio de Janeiro",
            "city" : "Volta Redonda",
            "zip_code" : "27275-595",
            "street" : "Servidão B-1",
            "number" : "1106"
        }
    },
    "card":{
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "number": "41111111111111",
        "cvv": "123",
        "capture": false
    },
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```

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
        "document_type" : "CUIT",
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
        "document_type": "CUIT",
        "cbu": "00700415-20000021948168",
        "reference": "43423245",
        "amount_to_transfer": 150.01
    },
    "created_date" : "2018-02-15T15:44:42.310Z",
    "approved_date" : "2018-02-15T15:44:42.310Z",
    "status" : "PENDING",
    "status_detail" : "The payment is pending.",
    "status_code" : "100",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
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
    "status" : "PENDING",
    "status_code" : "100",
    "status_detail" : "The payment is pending."
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
| `REJECTED` | 316 | Unsoported operation. |
| `REJECTED` | 317 | Rejected due to high risk. |
| `REJECTED` | 318 | Invalid transaction. |

### Errors

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

#### Http Errors {#http-errors}

| **HTTP Status Code** | **Error Code** | **Error Detail** |
| :--- | :--- | :--- |
| `403 Forbidden` | 3001 | Invalid Credentials. |
|  | 3002 | Unregistered IP address. |
|  | 3003 | Merchant has no authorization to use this API. |
| `404 Not Found` | 4000 | Payment not found. |
| `400 Bad Request` | 5000 | Invalid request. |
|  | 5001 | Invalid param. |
|  | 5002 | Invalid transaction status. |
|  | 5003 | Country not supported. |
|  | 5004 | Currency not allowed for this country. |
|  | 5005 | User unauthorized due to cadastral situation. |
|  | 5006 | User limit exceeded. |
|  | 5007 | Amount exceeded. |
|  | 5008 | Token not found or inactive. |
| `429 Too many requests` | 6000 | Too many requests to the api \(Not implemented yet\). |
| `500 Internal Server Error` | 7000 | The input is correct, but dLocal fails to process the payment. Rare case. |

## Notifications

Notifications will be sent in every change of status of a payment to the notification URL specified by the merchant. This URL is taken from the `notification_url` field of the payment, if it differs from the one specified in the merchant panel. The body of the request will always be the payment object.

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
        "document_type" : "CUIT",
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
        "document_type": "CUIT",
        "cbu": "00700415-20000021948168",
        "reference": "43423245",
        "amount_to_transfer": 150.01
    },
    "created_date" : "2018-02-15T15:14:52-00:00",
    "status" : "PENDING",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```

