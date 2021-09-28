---
description: Learn how to retrieve account structure information.
---

# Get account information

Retrieve account structure information such as owner, creation date, balance, and associated cards. Usually used to retrieve basic data and present account information to the user on the app's main page.

You will **need it to check account status after receiving asynchronous notifications**.

{% api-method method="get" host="https://issuing-api.dlocal.com" path="/issuing/accounts/{account\_id}" %}
{% api-method-summary %}
Get account information
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="account\_id" type="string" required=true %}
Account ID provided when the account was created.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "account_id": "ISGA-4-e225325f3bdb4f6d868403f7c7225b05",
    "country": "CO",
    "currency": "COP",
    "account_reference": "X7g67l1Ce0",
    "status": "ACTIVE",
    "owner": {
        "first_name": "John",
        "last_names": "Smith",
        "birth_date": "08-01-1957",
        "email": "john@dlocal.com",
        "phone_number": "46044490",
        "document": "3504171865",
        "address": {
            "country": "CO",
            "city": "Medellin",
            "state": "Antioquia",
            "street": "Carrera 74 xgvbYJ",
            "street2": "Carrera 74 KboFkX",
            "house_number": "52",
            "zip_code": "05001000",
            "neighbourhood": "El Poblado"
        },
        "marital_status": "S",
        "gender": "M",
        "birth_place": "Colombia",
        "document_type": "CC",
        "nationality": "Colombian"
    },
    "description": "dLocal Wallet for John Smith",
    "creation_date": "2021-03-09T17:02:28Z",
    "notification_url": "http://merchant.dlocal.com/notification",
    "cards": [
        {
            "card_id": "ISGC-4-4fe44bfbb9234e0ca78d69b42f7b8d06",
            "type": "PHYSICAL",
            "created_at": "2021-03-09T17:02:33Z"
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Account status

### All countries

| Status | Description |
| :--- | :--- |
| `PENDING` | Account created but awaiting validation. |
| `INACTIVE` | Account validated but not activated. |
| `ACTIVE` | Account created and activated correctly. |
| `REJECTED` | Account rejected. |

### Brazil

| Status | Description |
| :--- | :--- |
| `WAITING_FOR_IMAGES` | KYC images must be sent. |

### Colombia

| Status |  Description |
| :--- | :--- |
| `WAITING_FOR_OTP_EMAIL` | OTP Code email must be sent. |
| `WAITING_FOR_OTP_PHONE` | OTP Code phone must be sent.  |

{% hint style="info" %}
The OTP code sent by dLocal will be valid for 5 minutes.
{% endhint %}

