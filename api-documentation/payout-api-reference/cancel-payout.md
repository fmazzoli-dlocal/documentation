# Cancel payout

{% api-method method="post" host="https://api.dlocal.com/api\_curl/cashout\_api" path="/cancel\_cashout" %}
{% api-method-summary %}
Cancel payout
{% endapi-method-summary %}

{% api-method-description %}
This function cancels a payout. Only payouts with 'Pending' status can be cancelled.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="login" type="string" required=true %}
Your merchant ID in dLocal platform   
\(length: 32 chars\)  
Example: AsGsd35Grf
{% endapi-method-parameter %}

{% api-method-parameter name="pass" type="string" required=true %}
Your merchant password in dLocal platform   
\(length: 32 chars\)  
Example: D23weF2f4g
{% endapi-method-parameter %}

{% api-method-parameter name="external\_id" type="string" required=true %}
Payout identification \(at the merchant site\)  
\(Max. 100 chars\)  
Example: payout1234
{% endapi-method-parameter %}

{% api-method-parameter name="cashout\_id" type="string" required=true %}
Payout identification \(at dLocal site\)  
\(Max. 10 chars\)  
Example: 10050
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Payout cancelled
{% endapi-method-response-example-description %}

```text
{
“status”: 0,
“description”: “OK”
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
**For fields 'login' & 'pass':**

**x\_login** and **x\_trans\_key** are your credentials. Remember to find them in the panel, section Integration -&gt; Credentials & Settings.
{% endhint %}

