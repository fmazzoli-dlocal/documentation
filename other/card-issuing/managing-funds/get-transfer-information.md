# Get Transfer Information

This function enables to retrieve account structure information such as transfer Id, amount, currency and status.

You will need it to check transfer status after receiving asynchronous notification.

{% api-method method="get" host="https://sandbox.dlocal.com" path="/issuing/transfers/{transfer\_id}" %}
{% api-method-summary %}
Get Transfer Information
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="transfer\_id" type="string" required=true %}
Transfer id provided when transfer was created.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "currency": "COP",
    "amount": 106,
    "transfer_description": "Transfer fund decription",
    "notification_url": "http://merchant.dlocal.com/notification",
    "merchant_reference": "t4J0RQgsnO",
    "destination_account_id": "ISGA-4-a75663b8b0924dbbb62cfd895d11aa80",
    "transfer_type": "DISBURSEMENT",
    "date": "2021-03-11T18:12:28Z",
    "status": "APPROVED",
    "transfer_id": "ISGT-4-d9f327b84b5d40adaf59160ee87133f0"
} 
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Transfer status

The transfer status can take one of the following values:

| Code | Description | Description |
| :--- | :--- | :--- |
| 0 | Received | The transfer is received to be processed in the next cut off |
| 1 | Completed | The transfer was completed |
| 2 | Cancelled | The transfer was cancelled by merchant |
| 3 | Rejected | The transfer was rejected |
| 4 | Delivered | The transfer is being processed  |
| 5 | On hold | The transfer is on hold by the merchant or awaiting for further legal information to be processed |

