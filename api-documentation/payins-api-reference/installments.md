# Installments

You can specify an installment plan, to guarantee the surcharge per installment that will be charged.

## The Installment Plan Object

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
    "currency" : "BRL",
    "bin" : "435921",
    "amount": 1500.00,
    "installments" : [
        {
            "id" : "INS54434-3",
            "installment_amount" : 550.00,
            "installments" : 3,
            "total_amount" : 1650.00
        },
        {
            "id" : "INS54434-6",
            "installment_amount" : 350.00,
            "installments" : 6,
            "total_amount" : 2100.00
        },
        {
            "id" : "INS54434-8",
            "installment_amount" : 250.00,
            "installments" : 12,
            "total_amount" : 3000.00
        }
    ]
}
```
{% endtab %}
{% endtabs %}

## The Installment Object

{% tabs %}
{% tab title="Installment Object" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | String | The installment id |
| `installment_amount` | Positive Float | Instalment amount. |
| `total_amount` | Positive Float | Instalments total amount. |
| `installments` | Integer | Number of installments. |
{% endtab %}

{% tab title="Example Installment Object" %}
```yaml
{
"id" : "INS54434-3",
"installment_amount" : 550,
"installments" : 3,
"total_amount" : 1650
}
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.dlocal.com/" path="installments-plans" %}
{% api-method-summary %}
Create an Installment Plan
{% endapi-method-summary %}

{% api-method-description %}
Create an installments plan.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="country" type="string" required=true %}
The country of the installment plan.
{% endapi-method-parameter %}

{% api-method-parameter name="bin" type="string" required=true %}
The credit card bin.
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="number" required=true %}
The amount of the installment plan. Decimal.
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
    "amount": 1500.00,
    "currency" : "BRL",
    "installments" : [
        {
            "id" : "INS54434-3",
            "installment_amount" : 550.00,
            "installments" : 3,
            "total_amount" : 1650.00
        },
        {
            "id" : "INS54434-6",
            "installment_amount" : 350.00,
            "installments" : 6,
            "total_amount" : 2100.00
        },
        {
            "id" : "INS54434-8",
            "installment_amount" : 250.00,
            "installments" : 12,
            "total_amount" : 3000.00
        }
    ]
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
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d {body}
    https://api.dlocal.com/installments-plans
```

### Example request body

```yaml
{
    "country" : "BR",
    "bin" : "435921",
    "amount": 30,
    "currency" : "BRL"
}
```

