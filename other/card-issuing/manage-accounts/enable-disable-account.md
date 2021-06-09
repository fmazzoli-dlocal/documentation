# Enable/Disable Account

This function is used to enable and disable an account. 

Disabled accounts will not allow:

* Issuing cards
* Top ups
* Incoming or outgoing transfers

As an example, you can use this function to disable if fraud is suspected or if user requests to freeze balance.

{% api-method method="patch" host="https://sandbox.dlocal.com" path="/issuing/accounts/{account\_id}" %}
{% api-method-summary %}
Enable/Disable Account
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

