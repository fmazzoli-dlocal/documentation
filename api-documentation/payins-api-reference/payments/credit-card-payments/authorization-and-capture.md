# Authorization and Capture

Authorizing a card payment allows you to reserve funds in a customer's bank account, days before the actual payment occurs – for example when making hotel reservations or booking car rentals.

It's a two-step process. First you need to create an _Authorization_, and then you need to _Capture_ it.

## Create an Authorization

To create an authorization, simply create a regular [card payment](./) with the parameter `capture` = `FALSE` within the `card` object.

### Example Authorization

{% tabs %}
{% tab title="Example Authorization Request" %}
```bash
$ curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'X-Version: 2.1' \
    -H 'User-Agent: MerchantTest / 1.0 ' \
    -H 'Content-Type: application/json' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/secure_payments
```

```yaml
{
    "amount": 120,
    "currency" : "USD",
    "country": "BR",
    "payment_method_id" : "CARD",
    "payment_method_flow" : "DIRECT",
    "payer":{
        "name" : "Thiago Gabriel",
        "email" : "thiago@example.com",
        "document" : "53033315550"
    },
    "card":{
        "holder_name" : "Thiago Gabriel",
        "number" : "4111111111111111",
        "cvv" : "123",
        "expiration_month" : 10,
        "expiration_year" : 2040,
        "capture" : "false"
    },
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}

{% tab title="Example Authorization Response" %}
```yaml
{
    "id": "D-4-e2227981-8ec8-48fd-8e9a-19fedb08d73a",
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
    "created_date": "2019-02-06T21:04:43.000+0000",
    "approved_date": "2019-02-06T21:04:44.000+0000",
    "status": "AUTHORIZED",
    "status_detail": "The payment was authorized",
    "status_code": "600",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}

The `id` returned corresponds to the unique identifier of the Authorization \(`authorization_id`\)

## Capture an Authorization

{% api-method method="post" host="https://api.dlocal.com" path="/payments" %}
{% api-method-summary %}
Capture an Authorization
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="authorization\_id" type="string" required=true %}
ID of the Authorization to be captured.
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="number" required=false %}
Amount to be captured \(in the currency specified in `currency`\). Must be equal or less than the authorized amount.  
**If not included, the capture will be for the total amount of the authorization.**
{% endapi-method-parameter %}

{% api-method-parameter name="currency" type="string" required=false %}
Transaction currency in ISO 4217 \(see http://en.wikipedia.org/wiki/ISO\_4217\). Each country accepts USD and local currency.  
**Required if amount is present.**
{% endapi-method-parameter %}

{% api-method-parameter name="order\_id" type="string" required=false %}
ID of the capture given by the merchant in their system. Think of it as an external id of the capture.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
    "id": "D-4-09f52dd0-5cfa-4b0e-a471-1608ea0dba24",
    "amount": 120,
    "currency": "USD",
    "country": "BR",
    "created_date": "2019-02-07T13:47:06.000+0000",
    "approved_date": "2019-02-07T13:47:06.000+0000",
    "status": "PAID",
    "status_detail": "The payment was paid",
    "status_code": "200",
    "order_id": "657434343-1",
    "authorization_id": "D-4-e2227981-8ec8-48fd-8e9a-19fedb08d73a"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Example Capture

{% tabs %}
{% tab title="Example Capture Request" %}
```bash
$ curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'X-Version: 2.1' \
    -H 'User-Agent: MerchantTest / 1.0 ' \
    -H 'Content-Type: application/json' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/payments
```

```yaml
{
    "authorization_id": "D-4-e2227981-8ec8-48fd-8e9a-19fedb08d73a",
    "amount": 120,
    "currency": "USD",
    "order_id": "657434343-1"
}
```
{% endtab %}

{% tab title="Example Capture Response" %}
```yaml
{
    "id": "D-4-09f52dd0-5cfa-4b0e-a471-1608ea0dba24",
    "amount": 120,
    "currency": "USD",
    "country": "BR",
    "created_date": "2019-02-07T13:47:06.000+0000",
    "approved_date": "2019-02-07T13:47:06.000+0000",
    "status": "PAID",
    "status_detail": "The payment was paid",
    "status_code": "200",
    "order_id": "657434343-1",
    "authorization_id": "D-4-e2227981-8ec8-48fd-8e9a-19fedb08d73a"
}
```
{% endtab %}
{% endtabs %}

The `id` returned corresponds to the unique identifier of the Captured payment. Some countries allow multiple partial captures per Authorization. Contact your Technical Account Manager for more details.

## Authorization Cancellation

An authorization can be cancelled before it is captured if the payment is no longer needed.

{% api-method method="post" host="https://api.dlocal.com/payments/" path="{authorization\_id}/cancel" %}
{% api-method-summary %}
Cancel an Authorization
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="authorization\_id" type="string" required=true %}
The Authorization id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
    "id": "D-4-09f52dd0-5cfa-4b0e-a471-1608ea0dba24",
    "amount": 120,
    "currency": "USD",
    "payment_method_id": "CARD",
    "payment_method_type": "CARD",
    "payment_method_flow": "DIRECT",
    "country": "BR",
    "created_date": "2019-02-07T17:37:36.000+0000",
    "approved_date": "2019-02-07T17:37:36.000+0000",
    "status": "CANCELLED",
    "status_detail": "The payment was cancelled",
    "status_code": "400",
    "order_id": "be2fbac6-6114-44dc-a5f5-c4cdc38dda57",
    "notification_url": "http://conductor.sandbox.internal/robot-server/rest/generic/notification/new"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Example Cancel 

{% tabs %}
{% tab title="Example Cancel Request" %}
```bash
$ curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'X-Version: 2.1' \
    -H 'User-Agent: MerchantTest / 1.0 ' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/payments/D-4-09f52dd0-5cfa-4b0e-a471-1608ea0dba24/cancel    
```
{% endtab %}

{% tab title="Example Cancel Response" %}
```yaml
{
    "id": "D-4-09f52dd0-5cfa-4b0e-a471-1608ea0dba24",
    "amount": 120,
    "currency": "USD",
    "payment_method_id": "CARD",
    "payment_method_type": "CARD",
    "payment_method_flow": "DIRECT",
    "country": "BR",
    "created_date": "2019-02-07T17:37:36.000+0000",
    "approved_date": "2019-02-07T17:37:36.000+0000",
    "status": "CANCELLED",
    "status_detail": "The payment was cancelled",
    "status_code": "400",
    "order_id": "be2fbac6-6114-44dc-a5f5-c4cdc38dda57",
    "notification_url": "http://conductor.sandbox.internal/robot-server/rest/generic/notification/new"
} 
```
{% endtab %}
{% endtabs %}

## $0 Authorization

Use a $0 Authorization to valide the user's card. You need to create an Authorization as explained above, but with `amount` = `0` and `verify` = `true` within the `card` object:

{% tabs %}
{% tab title="Request Example" %}
Request example:

```yaml
{
    "amount": 0,
    "currency": "BRL",
    "country": "BR",
    "payment_method_id": "CARD",
    "payment_method_flow": "DIRECT",
    "payer": {
        "name": "MXFGpBEw AJsGTALt",
        "email": "0yesa0xbd3g2-autest@dlocal.com",
        "phone": "4832695335",
        "address": {
            "country": "BR",
            "state": "Santa Catarina",
            "city": "Florianopolis",
            "zip_code": "88058",
            "street": "Rodovia Armando Calil Bulos",
            "number": "5940"
        },
        "document": 26410722
    },
    "card": {
        "holder_name" : "Thiago Gabriel",
        "expiration_month": 7,
        "expiration_year": 2024,
        "brand": "Visa",
        "verify": true,
        "capture": false,
        "cvv": "***",
        "number": "42976**********"
    },
    "order_id": "BENtest-h8fJ8blUTjY",
    "description": "LO4nLkTqt2tt",
    "notification_url": "https://postman-echo.com/post"
}
```
{% endtab %}

{% tab title="Response Example" %}
Response Example:

```yaml
{
    "id": "T-40004-eebc14d9-8381-4bf6-b8b7-82acbb06f166",
    "amount": 0,
    "currency": "BRL",
    "payment_method_id": "CARD",
    "payment_method_type": "CARD",
    "payment_method_flow": "DIRECT",
    "country": "BR",
    "card": {
        "holder_name" : "Thiago Gabriel",
        "expiration_month": 7,
        "expiration_year": 2024,
        "brand": "VI",
        "last4": "8528",
        "verify": true
    },
    "created_date": "2020-09-29T17:42:40.000+0000",
    "approved_date": "2020-09-29T17:42:40.000+0000",
    "status": "VERIFIED",
    "status_detail": "The payment was verified.",
    "status_code": "700",
    "order_id": "BENtest-h8fJ8blU",
    "description": "LO4nLkTqt2tt",
    "notification_url": "https://postman-echo.com/post",
}
```
{% endtab %}
{% endtabs %}

## Refunds for Captures

**Refunds are applied to the Captures, not the Authorization**. 

{% api-method method="post" host=" https://api.dlocal.com/" path="refunds" %}
{% api-method-summary %}
Make a Refund
{% endapi-method-summary %}

{% api-method-description %}
On the`payment_id` parameter, make sure to include the `id` of the Capture, not the Authorization.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="payment\_id" type="string" required=true %}
The id of the **capture**.
{% endapi-method-parameter %}

{% api-method-parameter name="notification\_url" type="string" required=true %}
If a refund is pending, the refund confirmation is sent asynchronously to this URL.
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="number" required=false %}
Amount to refund. If the amount is empty, then the default is total amount of the payment.  
**Required if** `currency` **is present.**
{% endapi-method-parameter %}

{% api-method-parameter name="currency" type="string" required=false %}
Currency of the Amount.  
**Required if** `amount` **is present.**
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
Description of the refund.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "id" : "REF42342",
   "payment_id" : "D-4-09f52dd0-5cfa-4b0e-a471-1608ea0dba24",
   "notification_url" : "http://some.url",
   "amount" : 803.04,
   "currency" : "BRL",
   "status" : "SUCCESS",
   "status_code" : 200,
   "status_detail" : "The refund was paid",
   "created_date" : "2018-09-06T22:03:03.000+0000",
   "amount_refunded" : 803.04
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Read more about Refunds [here](../../refunds.md).

