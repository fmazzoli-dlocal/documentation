# Release payout



{% api-method method="post" host="https://api.dlocal.com/api\_curl/cashout\_api" path="/release\_cashout" %}
{% api-method-summary %}
Release payout
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to release a payout form On hold status so that it can be processed. Note that **only payouts with 'On hold' status** can be released. **The service will not release the payout if it is in On Hold state due to fraud compliance.**
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
Payout released
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

**x\_login** and **x\_trans\_key** are your credentials. Remember to find them in the [Merchant Panel](https://merchant.dlocal.com/login), under the Integration &gt; Credentials & Settings section. 
{% endhint %}

**Example request body:**  


```text
{
   "external_id": "arf2563",
   "cashout_id": "234562262",
   "login": "qr122vs",
   "pass": "q2w34t",
   "type": "json"
}

```

  


