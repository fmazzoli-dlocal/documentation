# Transaction History

This function enables retrieving detailed transaction history. The objects are sorted in descending order by creation date, with the most recently created object appearing first. Usually used to present to user in-app balance changes such as payments, top ups and transfers. 

### Transaction Object <a id="transaction-object"></a>

| Property | **Type** | **Description** |
| :--- | :--- | :--- |
| `transaction_id` | String | Unique identifier for the transaction. |
| `status` | String | The current status of the transaction. |
| `description` | String | Description of the transaction. |
| `type` | String | The nature of the transaction \(debit / credit\). |
| `created_date` | String | Time at which the transaction was created. _Note: transactions are in local time._  |
| `amount` | Integer | The total amount that was authorized or rejected. |
| `currency` | String | Three-letter [ISO currency code](https://www.iso.org/iso-4217-currency-codes.html). |
| `card_id` | String | Card associated with this authorization. |
| `card_acceptor` | Object | Seller information object.  |

#### \*card\_acceptor <a id="headers"></a>

| Property | **Type** | **Description** |
| :--- | :--- | :--- |
| `mid` | String | Identifier for the seller. |
| `mcc` | String | The merchant category code for the seller’s business |
| `category` | String | A categorization of the seller’s type of business. |
| `name` | String | Name of the seller. |
| `zip_code` | String | ZIP code where the seller is located.  |
| `state` | String | State where the seller is located. |
| `street` | String | Street where the seller is located. |
| `city` | String | City where the seller is located. |
| `country` | String | Country where the seller is located. |

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
{% api-method-parameter name="page\_size" type="integer" required=false %}
Limit of transactions to retreive. Default is 100 and max is 500
{% endapi-method-parameter %}

{% api-method-parameter name="page\_number" type="integer" required=false %}
Transaction start. By default 0
{% endapi-method-parameter %}

{% api-method-parameter name="start\_date" type="string" required=false %}
Transactions created after and equals this date. YYYY-MM-DD
{% endapi-method-parameter %}

{% api-method-parameter name="end\_date" type="string" required=false %}
Transactions created before and equals this date. YYYY-MM-DD
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
"transactions":[
       {
            "transaction_id": "ISGC-4-1JEqoK2eZvKYlo2CGGaCQ8Xn",
            "status": "APPROVED",
            "description": "Deposit",
            "type": "credit",
            "created_date": "2021-03-10T10:02:21.898Z",
            "amount": 5126,
            "currency": "COP",
            "card_id": "",
            “card_acceptor”: {
                “mid”: “”,
                “mcc”: “”,
                “category”: “”,
                “name”: “”,
                “zip_code”: “”,
                “state”: “”,
                “street”: “”,
                “city”: “”,
                “country”: “”
            }
        },  
      {
            "transaction_id": "ISGC-4-1LTqoK2eZvKYasdCGGaCQ8Xn",
            "status": "APPROVED",
            "type": "debit",
            "description": "Payment",
            "created_date": "2021-03-09T17:02:21.898Z",
            "amount": 1428,
            "currency": "COP",
            "card_id": "ISGC-4-a635217734a746dd9f3875899492c3aa",
            “card_acceptor”: {
                “mid”: "000000000032111",
                “mcc”: "6411",
                “category”: "computer_software_stores",
                “name”: "Computer Shop",
                “zip_code”: "110111",
                “state”: "CA",
                “street”: "Carrera 74",
                “city”: "Bogota",
                “country”: "CO"
            }
        }           
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

