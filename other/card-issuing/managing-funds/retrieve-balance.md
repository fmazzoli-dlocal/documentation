# Retrieve Balance

This function enables retrieving account balance.

{% api-method method="get" host="https://issuing-api.dlocal.com" path="/issuing/accounts/{account\_id}/transactions" %}
{% api-method-summary %}
Retrieve Balance
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="account\_id" type="string" required=true %}
Account id provided when account-owner was created
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "account_id": "ISGA-4-85e2b96385a3418dae1e5905f7893426",
    "country": "CO",
    "currency": "COP",
    "balance": 1812,
    "account_reference": "LCZjc0VGcU",
    "status": "ACTIVE"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



