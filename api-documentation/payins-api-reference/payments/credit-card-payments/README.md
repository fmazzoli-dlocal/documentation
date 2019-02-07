# Credit Card Payments

For credit card payments you can use the card information only if you business is [Full PCI DSS compliant](https://docs.dlocal.com/solutions/payins#pci-compliance). Otherwise you need to securely collect the card information using [Smart Fields](https://docs.dlocal.com/products/smart-fields).   
For recurring payments, first [save the card](https://docs.dlocal.com/api-documentation/payins-api-reference/saving-cards#create-a-card), and then use the `card_id` to charge the card.

{% hint style="info" %}
**Important**: If you are making a payment **with credit card information**, you need to use the following endpoint:   
h**ttps://api.dlocal.com/secure\_payments**

Card payments with a `card_id` or `token` should use the endpoint: **https://api.dlocal.com/payments**
{% endhint %}

{% api-method method="post" host="https://api.dlocal.com" path="/payments" %}
{% api-method-summary %}
Create a Card Payment
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

{% api-method-parameter name="payment\_method\_id" type="string" required=true %}
Always send **`CARD`** for card payments.
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
**Required only for** `DIRECT` **payment\_method\_flow.**
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
| `document` | String | User’s personal identification number. [Click here for more details.](../../country-reference.md#documents) **Required**. |
| `user_reference` | String | Unique user id at the merchant side. Optional. |
| `address` | [Address Object ](../#the-address-object) | User’s address. **Only required in India.** |
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

For credit card payments you can use the card information only if you business is [Full PCI DSS compliant](../../../../solutions/payins.md#pci-compliance). Otherwise you need to collect the card information using [Smart Fields](../../../../products/smart-fields/). For recurring payments, first [save the card](../../saving-cards.md#create-a-card), and then use the `card_id` to charge the card.

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
| `token` | String | Temporary credit card token securely created using [Smart Fields](../../../../products/smart-fields/). Optional. |
| `cvv_token` | String | Temporary CVV token securely created using the CVV-only Smart Field. |
| `card_id` | String | Credit card id returned by the [Create a Card ](../../saving-cards.md#create-a-card)call. Optional. |
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



## Pay with Card information 

The following example applies for credit card payments using the plain credit card information \(**only for Full PCI DSS merchants**\). To make payments using encrypted card information, simply **replace** the `number`and `cvv`parameters with [`encrypted_data`](https://docs.dlocal.com/api-documentation/payins-api-reference/security#sensitive-data-encryption).

{% tabs %}
{% tab title="Example Request" %}
#### Example Request <a id="example-request-3"></a>

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

#### Example Request Body <a id="example-request-body"></a>

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

{% tab title="Example Response" %}
#### Example Response

```yaml
{
    "id": "D-4-cf8eef6b-52d5-4320-b5ea-f5e0bbe4343f",
    "amount": 120,
    "currency": "USD",
    "payment_method_id": "CARD",
    "payment_method_type": "CARD",
    "payment_method_flow": "DIRECT",
    "country": "BR",
    "card": {
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "brand": "VI",
        "last4": "1111"
    },
    "created_date": "2018-12-26T20:26:09.000+0000",
    "approved_date": "2018-12-26T20:26:09.000+0000",
    "status": "PAID",
    "status_detail": "The payment was paid",
    "status_code": "200",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}

## Pay with [ Smart Fields](../../../../products/smart-fields/)

The following example applies for credit card payments using a [Smart Fields](../../../../products/smart-fields/fields-setup-guide.md) `token`.

{% tabs %}
{% tab title="Example Request" %}
#### Example Request <a id="example-request-4"></a>

```bash
curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Content-Type: application/json' \
    -H 'X-Version: 2.1' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/payments
```

#### Example Request Body <a id="example-request-body-1"></a>

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

{% tab title="Example Response" %}
#### Example Response

```yaml
{
    "id": "D-4-80ca7fbd-67ad-444a-aa88-791ca4a0c2b2",
    "amount": 120,
    "currency": "USD",
    "payment_method_id": "CARD",
    "payment_method_type": "CARD",
    "payment_method_flow": "DIRECT",
    "country": "BR",
    "card": {
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "brand": "VI",
        "last4": "1111"
    },
    "created_date": "2018-12-26T20:28:47.000+0000",
    "approved_date": "2018-12-26T20:28:47.000+0000",
    "status": "PAID",
    "status_detail": "The payment was paid",
    "status_code": "200",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}

## Pay with Saved Card

The following example applies for credit card payments using a the `card_id` gotten in the [Create a Card method.](../../saving-cards.md#create-a-card)​​

{% tabs %}
{% tab title="Example Request" %}
#### Example Request <a id="example-request-4"></a>

```bash
curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Content-Type: application/json' \
    -H 'X-Version: 2.1' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/payments
```

#### Example Request Body <a id="example-request-body-1"></a>

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
        "card_id": "CID-124c18a5-874d-4982-89d7-b9c256e647b5"
    },
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}

{% tab title="Example Response" %}
#### Example Response​

```yaml
{
    "id": "D-4-80ca7fbd-67ad-444a-aa88-791ca4a0c2b2",
    "amount": 120,
    "currency": "USD",
    "payment_method_id": "CARD",
    "payment_method_type": "CARD",
    "payment_method_flow": "DIRECT",
    "country": "BR",
    "card": {
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "brand": "VI",
        "last4": "1111"
    },
    "created_date": "2018-12-26T20:28:47.000+0000",
    "approved_date": "2018-12-26T20:28:47.000+0000",
    "status": "PAID",
    "status_detail": "The payment was paid",
    "status_code": "200",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}

## Other Card Payment Operations

* [Authorization and Capture](authorization-and-capture.md)
* [Chargebacks](chargebacks.md)
* [3D-Secure](3d-secure.md)

