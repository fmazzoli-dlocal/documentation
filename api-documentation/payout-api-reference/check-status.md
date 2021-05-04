---
description: This function checks the status of a payout
---

# Check status

{% api-method method="post" host="https://api.dlocal.com/api\_curl/cashout\_api" path="/check\_status\_cashout" %}
{% api-method-summary %}
 Check status
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to check the payout status
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
Payout identification \(at the merchant site\)\*  
\(Max. 100 chars\)  
Example: payout1234
{% endapi-method-parameter %}

{% api-method-parameter name="cashout\_id" type="string" required=true %}
Payout identification \(at dLocal site\)\*  
\(Max. 10 chars\)  
Example: 10050
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Check\_status OK
{% endapi-method-response-example-description %}

```javascript
{
“status”: ”0”, 
“cash_out_status”: “[the status of the cashout]”,
“description”: “[the description of the status of the cashout]”,
“status_code”: “[if is status rejected, the reason code for the rejection]”,
“status_reason”: “[if is status rejected, the reason message for the rejection]”
} 

If the status is 0 then:

{    
    "status": 0,   
    "cash_out_status": 0,    
    "description": "Received"
}



IF the status is 1 then:
{
    "status": 1,
    "desc": "Invalid control string",
    "error_code": "302"
}




```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

* **\***The fields **external\_id** and **cashout\_id** are optional, but you **must send one or both.**

{% hint style="success" %}
**Response:**

If status = 0 --&gt; the **cash\_out\_status** field can take one of the [following values](error-codes-reference.md#payout-status)

If cash\_out\_status = 3 --&gt; the **status\_code** field can take one of the [following values](error-codes-reference.md#error-codes-range)
{% endhint %}

{% hint style="info" %}
**For fields 'login' & 'pass':**

**x\_login** and **x\_trans\_key** are your credentials. Remember to find them in the [Merchant Panel](https://merchant.dlocal.com/login), under the Integration &gt; Credentials & Settings section. 
{% endhint %}

