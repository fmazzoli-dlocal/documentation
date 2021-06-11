# Card Activation

This operation can be used for activating a registered card.

{% hint style="info" %}
Inform users that the **PIN** for card use is the **last 4 digits** of their **ID card**.
{% endhint %}

{% api-method method="post" host="https://sandbox.dlocal.com" path="/issuing/xxx" %}
{% api-method-summary %}
Card Activation
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="card\_id" type="string" required=true %}
card\_id provided when card was created
{% endapi-method-parameter %}

{% api-method-parameter name="lastDigits" type="string" required=true %}
last 6 digits of the Primary Account Number \(PAN\)
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

### 

