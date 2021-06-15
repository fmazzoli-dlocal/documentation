# Sent OTP Codes

This function is to send OTP Codes in order to provide necessary documentation to validate Email or Telephone Number. Only used for **Colombia**.



{% api-method method="post" host="https://issuing-api.dlocal.com" path="/issuing/accounts/{account\_id}/OTP" %}
{% api-method-summary %}
Sent OTP Codes
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="account\_id" type="string" required=true %}
Provided when account was created
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
ENUM \('EMAIL','PHONE'\)
{% endapi-method-parameter %}

{% api-method-parameter name="code" type="string" required=true %}
code sent to account owner.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "account_id": "ISGA-4-e225325f3bdb4f6d868403f7c7225b05,
    "type": "EMAIL",
    "status": "WAITING_OTP_PHONE"    
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### 

