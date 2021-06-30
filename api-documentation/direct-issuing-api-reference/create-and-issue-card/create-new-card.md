# Create New Card

This function allows to Create and Issue a New Card for an account-owner. The card is associated to the account and all transactions will be reflected on account's balance.

Card schemes are subject to availability. 

On response to card creation, you will receive a `card_id`, please store this value as it will be used for transacting.

{% api-method method="post" host="https://issuing-api.dlocal.com" path="/issuing/cards" %}
{% api-method-summary %}
Create New Card
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="terms\_and\_conditions\_accepted" type="boolean" required=true %}
Card's terms and conditions 
{% endapi-method-parameter %}

{% api-method-parameter name="ip\_address" type="string" required=true %}
Cardholder's IP Address 
{% endapi-method-parameter %}

{% api-method-parameter name="notification\_url" type="string" required=true %}
URL to receive webhook notification on status change
{% endapi-method-parameter %}

{% api-method-parameter name="card\_reference" type="string" required=false %}
Card reference on merchant side
{% endapi-method-parameter %}

{% api-method-parameter name="delivery\_address" type="object" required=false %}
If not provided will use same as provided in account creation. See address object specs on Create account-owner section.
{% endapi-method-parameter %}

{% api-method-parameter name="account\_id" type="string" required=true %}
Account id to which card is associated
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
enum\('PHYSICAL','VIRTUAL'\)
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "account_id": "ISGA-4-9618440e0abe4fcfa77575319e6eb7ec",
    "card_reference": "WCaM8vn1YMNJ",
    "delivery_address": {
        "country": "CO",
        "city": "Medellin",
        "state": "Antioquia",
        "street": "Carrera 74 cYdDao",
        "street2": "Carrera 74 biVvwb",
        "house_number": "52",
        "zip_code": "05001000",
        "neighbourhood": "El Poblado"
    },
    "notification_url": "http://merchant.dlocal.com/notification",
    "card_id": "ISGC-4-a635217734a746dd9f3875899492c3aa",
    "type": "PHYSICAL",
    "status": "PENDING",
    "created_at": "2021-03-11T13:46:35.922Z"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Example Request

```text
{
    "account_id": "ISGA-4-9618440e0abe4fcfa77575319e6eb7ec",
    "ip_address": "186.52.133.239",
    "type": "PHYSICAL",
    "card_reference": "WCaM8vn1YMNJ",
    "delivery_address": {
        "country": "CO",
        "city": "Medellin",
        "state": "Antioquia",
        "street": "Carrera 74 cYdDao",
        "street2": "Carrera 74 biVvwb",
        "house_number": "52",
        "zip_code": "05001000",
        "neighbourhood": "El Poblado"
    },
    "terms_and_conditions_accepted": "T",
    "notification_url": "http://merchant.dlocal.com/notification"
}
```

#### Asynchronous Notifications

When there is a change of status for the card, we will send you a notification to the provided `notification_url` indicating card`_id` . You will need to call [Get Card Information]() function to review this changes.

```text
{ 
    "card_id":"ISGC-4-a635217734a746dd9f3875899492c3aa", 
    "account_id": "ISGA-4-9618440e0abe4fcfa77575319e6eb7ec" 
}
```

#### 

