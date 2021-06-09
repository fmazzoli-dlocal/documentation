# Block/Unblock Card

This function is used to modify the status of a card. The possible status are ACTIVE, INACTIVE, CANCELED. 

In Colombia, it is only possible to deactivate \(block\) cards via API. Unblocking must be done offline with provider.

{% api-method method="patch" host="https://sandbox.dlocal.com" path="/issuing/cards/{card\_id}" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="card\_id" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="status" type="string" required=true %}
ACTIVE, INACTIVE or CANCELED
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



