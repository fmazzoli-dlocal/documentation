---
description: See all the information of a transfer.
---

# Get transfer information

This function enables to **retrieve account structure information** such as amount, currency, and status through the transfer ID.

You will need it to check the transfer status after receiving an asynchronous notification.

{% api-method method="get" host="https://issuing-api.dlocal.com" path="/issuing/transfers/{transfer\_id}" %}
{% api-method-summary %}
Get transfer information
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="transfer\_id" type="string" required=true %}
Transfer ID provided when the transfer was created.
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

## Transfer status

The transfer status can take one of the following values:

| Code | Status | Description |
| :--- | :--- | :--- |
| 0 | `RECEIVED` | Transfer received by dLocal and is now pending to be processed. |
| 1 | `COMPLETED` | Transfer completed and confirmed by the card issuer bank. |
| 2 | `CANCELLED` | Transfer canceled by the merchant. |
| 3 | `REJECTED` | Transfer rejected by the card issuer bank. |
| 4 | `DELIVERED` | Transfer sent to the user card but it was not confirmed yet. |
| 5 | `ON HOLD` | Transfer is on hold by the merchant or awaiting for further legal information to be processed. |

