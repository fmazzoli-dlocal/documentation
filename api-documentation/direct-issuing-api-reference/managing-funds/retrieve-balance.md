---
description: See all the information of a balance.
---

# Retrieve balance

This function enables **retrieving account balance** through the account ID.

{% api-method method="get" host="https://issuing-api.dlocal.com" path="/issuing/accounts/{account\_id}/balance" %}
{% api-method-summary %}
Retrieve balance
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="account\_id" type="string" required=true %}
Account ID provided when account-owner was created.
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



