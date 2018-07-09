# Credit Card Payment Operations

{% api-method method="post" host="https://api.dlocal.com/payments/" path="{id}/capture" %}
{% api-method-summary %}
Capture a credit card payment
{% endapi-method-summary %}

{% api-method-description %}
Capture an existing, uncaptured payment. This is the second half of the two-step payment flow, where first you created a paymentwith the capture option set to false.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
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
        "token": "CV-e90078f7-e027-4ce4-84cb-534c877be33c",
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "last4": "1111",
        "brand": "VI",
        "capture": true
    },
    "created_date" : "2018-02-15T15:14:52-00:00",
    "approved_date" : "2018-02-15T15:17:52-00:00",
    "status" : "PAID",
    "status_detail" : "The payment was paid.",
    "status_code": 200,
    "external_reference": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Example request

```bash
$ curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/payments/PAY4334346343/capture
```

{% api-method method="post" host="https://api.dlocal.com/payments/" path="{id}/cancel" %}
{% api-method-summary %}
Cancel a credit card payment
{% endapi-method-summary %}

{% api-method-description %}
Cancel an existing, uncaptured payment. This is the second half of the two-step payment flow, where first you created a payment with the capture option set to false.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The payment id.
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
        "last4": "1111",
        "brand": "VI",
        "capture": false
    },
    "created_date" : "2018-02-15T15:14:52-00:00",
    "approved_date" : "2018-02-15T15:14:52-00:00",
    "status" : "CANCELLED",
    "status_detail" : "The payment was cancelled.",
    "status_code": 400,
    "external_reference": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Example Request

```bash
$ curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/payments/PAY4334346343/cancel
```

## Chargeback asynchronous notification

If a charge back was applied \(requested by the user\) a notification is sent to the merchant to the previously registered Merchant chargeback notification URL by POST protocol, sending the following parameters:

| **Property** | **Type** | **Description** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `id` | String | The chargeback id. |
| `payment_id` | String | The payment id. |
| `amount` | Positive Float | The amount of the chargeback. |
| `amount_chargedback` | Positive Float | The chargedback amount. |
| `currency` | String | The currency of the chargeback. |
| `status` | String | The status of the chargeback. |
| `status_code` | String | The [status](https://dlocal.com/docs/?language=cURL#chargeback-asynchronous-notification) code of the chargeback. |
| `created_date` | String | The date of when the chargeback was executed. |

**Example post**

POST: _{merchant.chargeback\_url}_

```yaml
{
    "id": "CHAR42342",
    "payment_id": "PAY245235",
    "amount": 100.00,
    "amount_chargedback": 100.00,
    "currency": "USD",
    "status": "SUCCESS",
    "status_code": 200,
    "created_date" : "2018-02-15T15:14:52-00:00"
}
```

### Chargeback status {#chargeback-status}

| **Status** | **Status code** | **Description** |
| --- | --- | --- |
| `PENDING` | 100 | The chargeback is pending. |
| `SUCCESS` | 200 | The chargeback was executed. |
