---
description: Learn how to activate a registered card.
---

# Activate card

This operation can be used for **activating a registered card**.

{% hint style="info" %}
Inform users that the **PIN for card use is the last 4 digits of their ID card.**
{% endhint %}

{% api-method method="post" host="https://issuing-api.dlocal.com" path="/issuing/cards/{card\_id}/activate" %}
{% api-method-summary %}
Card activation
{% endapi-method-summary %}

{% api-method-description %}
**Sandbox:** you can use any last digits code to active the card. If you want to test the error messages use the code: 000400.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="card\_id" type="string" required=true %}
Card ID provided when the card was created.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="last\_digits" type="string" required=true %}
Last 6 digits of the Primary Account Number \(PAN\).
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "card_id": "ISGC-4-51997ba1fa5f49d4b4881dfd6aa9b3d5",
    "type": "PHYSICAL",
    "status": "ACTIVE",
    "card_reference": "EPQFVL0jjS4R",
    "created_at": "2021-03-11T13:46:11Z"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

