---
description: Learn how to enable and disable an account.
---

# Enable/disable an account

You can use this function to disable an account if fraud is suspected or if the user requests to freeze balance.

{% api-method method="patch" host="https://issuing-api.dlocal.com" path="/issuing/accounts/{account\_id}" %}
{% api-method-summary %}
Enable/disable an account
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="account\_id" type="string" required=true %}
Account ID provided when the account was created.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="status" type="string" required=true %}
enum\('active', 'inactive'\)
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="warning" %}
Keep in mind that **disabled accounts will not allow issuing cards, top-ups, and incoming or outgoing transfers**.
{% endhint %}

