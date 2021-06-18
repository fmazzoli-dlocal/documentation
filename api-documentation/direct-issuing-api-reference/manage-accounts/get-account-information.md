# Get Account Information

This function enables to retrieve account structure information such as owner, creation date, balance and associated cards. Usually used to retrieve basic data and present account information to user on app main page.

You will need it to check account status after receiving asynchronous notification.

{% api-method method="get" host="https://issuing-api.dlocal.com" path="/issuing/accounts/{account\_id}" %}
{% api-method-summary %}
Get Account Information
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
    "balance": 0,
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

#### Account status

* PENDING - for account created but still not validated
* INACTIVE - Validated account but not activated
* ACTIVE - Active account, created correctly
* WAITING\_FOR\_IMAGES - KYC images must be sent \(only Brazil\)
* WAITING\_FOR\_OTP\_EMAIL - OTP Code EMAIL must be sent. The OTP code sent by dLocal will be valid for 5 minutes \(only Colombia\)
* WAITING\_FOR\_OTP\_PHONE - OTP Code PHONE must be sent.  The OTP code sent by dLocal will be valid for 5 minutes \(only Colombia\)
* REJECTED - Account was rejected

