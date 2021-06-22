# Transaction History

This function enables retrieving detailed transaction history. Usually used to present to user in-app balance changes such as payments, top ups and transfers. 

{% api-method method="get" host="https://issuing-api.dlocal.com" path="/issuing/accounts/{account\_id}/transactions" %}
{% api-method-summary %}
Transaction History
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

{% api-method-query-parameters %}
{% api-method-parameter name="limit" type="integer" required=false %}
Limit of transactions to retreive. Default is 100 and max is 500
{% endapi-method-parameter %}

{% api-method-parameter name="offset" type="integer" required=false %}
Transaction start. By default 0.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "account_id": "ISGA-4-85e2b96385a3418dae1e5905f7893426",
    "transactions": [
        {
            "status": "APPROVED",
            "type": "credit",
            "created_date": "2021-03-09T17:02:21.898Z",
            "amount": 1428,
            "currency": "COP"
        },
        {
            "status": "APPROVED",
            "type": "debit",
            "created_date": "2021-03-09T17:02:21.898Z",
            "amount": 1126,
            "currency": "COP"
        },
        {
            "status": "PENDING",
            "type": "debit",
            "created_date": "2021-03-09T17:02:21.898Z",
            "amount": 1574,
            "currency": "COP"
        },
        {
            "status": "APPROVED",
            "type": "debit",
            "created_date": "2021-03-09T17:02:21.898Z",
            "amount": 1829,
            "currency": "COP"
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



