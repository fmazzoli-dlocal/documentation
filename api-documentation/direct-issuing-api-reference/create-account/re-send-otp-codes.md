# Re send OTP Codes

This function is to re send OTP codes to the end user if they didn't receive it. Only used by **Colombia**.

{% hint style="info" %}
You can send up to 1 additional OTP code verification attempt via email or cellphone every 24 hours.
{% endhint %}

{% api-method method="post" host="https://issuing-api.dlocal.com" path="/issuing/accounts/{account\_id}/otp/resend" %}
{% api-method-summary %}
Re send OTP Codes
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

