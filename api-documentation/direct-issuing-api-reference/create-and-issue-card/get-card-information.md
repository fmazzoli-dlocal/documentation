---
description: See all the information of a card.
---

# Get card information

This function enables to **retrieve card information** such as status through the card ID.

You will need it to check account status after receiving asynchronous notifications.

{% api-method method="get" host="https://issuing-api.dlocal.com" path="/issuing/cards/{card\_id}" %}
{% api-method-summary %}
Get card information
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="card\_id" type="string" required=true %}
Card ID provided when the card was created.
{% endapi-method-parameter %}

{% api-method-parameter name="full\_data" type="boolean" required=false %}
Shows the card's sensitive data tokens. By default: false.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "account_id": "ISGA-4-5273636bbd604082928c81f1d99897b6",
    "card_id": "ISGC-4-970708fe1d1d45a78fdcfb6a6a2b111b",
    "type": "PHYSICAL",
    "status": "ACTIVE",
    "card_reference": "DFgH7CJTB1qF",
    "delivery_address": {
        "country": "CO",
        "city": "Medellin",
        "state": "Antioquia",
        "street": "Carrera 74 oZMwMG",
        "street2": "Carrera 74 AfYBwa",
        "house_number": "52",
        "zip_code": "05001000",
        "neighbourhood": "El Poblado"
    },
    "card_information": {
        "front_token": "AQICAHjajCjj_m_SHvhC9QhV2CT_N062EgS6-BUD2Ddfq2y_iAGoLHvoSHaQCwGSJOeFpyYwA",
        "rear_token": "AAAhjCBgwYJKoZIhvcNAQcGoHYwdAIBADBvBgkqhkiG9w0BBwEwHgYJYIZIAWUDBAEuMBEEDI1qTNda",
        "type": "IMAGE"
    },
    "created_at": "2021-03-11T20:33:33Z",
    "notification_url": "http://merchant.dlocal.com/notification"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
Please note that the endpoint retrieves the object `card_information_image` or `card_information_data` depending on the country. 

When you receive _`card_information_image`_ you get 2 tokens \(front and rear\) but when you receive _`card_information_data`_ you get 3 tokens \(CVV, PAN, expiration\).
{% endhint %}

## Card status

| Status | Description |
| :--- | :--- |
| `CREATED` | Card created but not activated. |
| `PENDING` | Card created and in process of delivery. |
| `ERROR` | Error in card creation, please retry or contact our support. |
| `INACTIVE` | Card not activated. |
| `ACTIVE` | Active card. |
| `BLOCKED` | Blocked card because was lost or stolen. |
| `CANCELLED` | Cancelled card. This status is permanent. |



