# Installments

When creating a card payment with installments, the Merchant will receive the **full amount** of the payment at settlement, with **no risks** involved.

To create a payment with installments, first you need to [create an Installments Plan](installments.md#create-an-installments-plan), to guarantee the surcharge per installment that will be charged.

With the Installment Plan id \( `installments_id` \) and the number of installments, you can go ahead and create a payment with installments.

{% api-method method="post" host="https://api.dlocal.com/" path="installments-plans" %}
{% api-method-summary %}
Create an Installments Plan
{% endapi-method-summary %}

{% api-method-description %}
Create an installments plan.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="country" type="string" required=true %}
The country of the installments plan.
{% endapi-method-parameter %}

{% api-method-parameter name="bin" type="string" required=true %}
The credit card bin.
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="number" required=true %}
The amount of the installments plan. Decimal.
{% endapi-method-parameter %}

{% api-method-parameter name="currency" type="string" required=true %}
The currency of the installments plan.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
    "id" : "INS54434",
    "country" : "BR",
    "bin" : "435921",
    "amount": 1000.00,
    "currency" : "BRL",
    "installments" : [
        {
            "id" : "INS54434-1",
            "installment_amount" : 1000.00,
            "installments" : 1,
            "total_amount" : 1000.00
        },
        {
            "id" : "INS54434-2",
            "installment_amount" : 550.00,
            "installments" : 2,
            "total_amount" : 1100.00
        },
        {
            "id" : "INS54434-3",
            "installment_amount" : 383.33,
            "installments" : 3,
            "total_amount" : 1150.00
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### The Installment Plan Object

{% tabs %}
{% tab title="Installment Plan Object" %}
| **Property** | Type | **Description** |
| :--- | :--- | :--- |
| `id` | String | The installments plan id. |
| `country` | String | The country of the installments plan. |
| `currency` | String | The currency of the installments plan. |
| `bin` | String | The credit card bin. |
| `amount` | Positive Float | The amount of the installments plan. |
| `installments` | [Installment Object](installments.md#the-installment-object)\[ \] | The installments plan information |
{% endtab %}

{% tab title="Example Installment Plan Object" %}
```yaml
{
    "id" : "INS54434",
    "country" : "BR",
    "bin" : "435921",
    "amount": 1000.00,
    "currency" : "BRL",
    "installments" : [
        {
            "id" : "INS54434-1",
            "installment_amount" : 1000.00,
            "installments" : 1,
            "total_amount" : 1000.00
        },
        {
            "id" : "INS54434-2",
            "installment_amount" : 550.00,
            "installments" : 2,
            "total_amount" : 1100.00
        },
        {
            "id" : "INS54434-3",
            "installment_amount" : 383.33,
            "installments" : 3,
            "total_amount" : 1150.00
        }
    ]
}
```
{% endtab %}
{% endtabs %}

### The Installment Object

{% tabs %}
{% tab title="Installment Object" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | String | The installment id. |
| `installment_amount` | Positive Float | Installment amount. Includes interests associated to the installment. |
| `total_amount` | Positive Float | Installments total amount. Includes interests associated to the installment. |
| `installments` | Integer | Number of installments. |
{% endtab %}

{% tab title="Example Installment Object" %}
```yaml
{
    "id" : "INS54434-2",
    "installment_amount" : 550.00,
    "installments" : 2,
    "total_amount" : 1100.00
}
```
{% endtab %}
{% endtabs %}

## Example Create Installment Plan

{% tabs %}
{% tab title="Example Create Installment Plan Request" %}
```bash
$ curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'X-Version: 2.1' \
    -H 'Content-Type: application/json' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/installments-plan
```

```yaml
{
    "country" : "BR",
    "bin" : "411111",
    "amount": 30,
    "currency" : "BRL"
}
```
{% endtab %}

{% tab title="Example Create Installment Plan Response" %}
```yaml
{
    "id" : "INS54434",
    "country" : "BR",
    "bin" : "435921",
    "amount": 1000.00,
    "currency" : "BRL",
    "installments" : [
        {
            "id" : "INS54434-1",
            "installment_amount" : 1000.00,
            "installments" : 1,
            "total_amount" : 1000.00
        },
        {
            "id" : "INS54434-2",
            "installment_amount" : 550.00,
            "installments" : 2,
            "total_amount" : 1100.00
        },
        {
            "id" : "INS54434-3",
            "installment_amount" : 383.33,
            "installments" : 3,
            "total_amount" : 1150.00
        }
    ]
}
```
{% endtab %}
{% endtabs %}

## Example Payment with Installments

{% tabs %}
{% tab title="Example Payment Request" %}
```bash
$ curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'X-Version: 2.1' \
    -H 'Content-Type: application/json' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/payments
```

```yaml
{
    "amount": 1000,
    "currency" : "BRL",
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
        "installments" : "3",
        "installments_id" : "INS54434"
    },
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}

{% tab title="Example Payment Response" %}
```yaml
{
    "id": "D-4-e2227981-8ec8-48fd-8e9a-19fedb08d73a",
    "amount": 1000.00,
    "currency": "BRL",
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
    "status": "PAID",
    "status_detail": "The payment was paid.",
    "status_code": "200",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}



