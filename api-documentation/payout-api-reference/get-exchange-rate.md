# Currency exchange

{% api-method method="post" host=" https://api.dlocal.com/api\_curl/cashout\_api" path="/get\_exchange\_rate" %}
{% api-method-summary %}
Get exchange rate
{% endapi-method-summary %}

{% api-method-description %}
This endpoint returns the exchange rate of the given currency in relation to one dollar \(USD\).
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

{% api-method-parameter name="currency" type="string" required=true %}
Currency to know the exchange rate  
\(Max. 3 chars\)  
Example: BRL
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Exchange rate OK
{% endapi-method-response-example-description %}

```javascript
{
“status”: 0,
"exchange_rate": 4.1234
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

