# Saving Cards

{% api-method method="post" host="https://api.dlocal.com/" path="secure\_cards" %}
{% api-method-summary %}
Create a Card
{% endapi-method-summary %}

{% api-method-description %}
Stores a card's information on dLocal's servers, and returns a card\_id, that can be used to make payments later on.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="country" type="string" required=true %}
Card's country
{% endapi-method-parameter %}

{% api-method-parameter name="card" type="object" required=true %}
The Card Object
{% endapi-method-parameter %}

{% api-method-parameter name="payer" type="object" required=true %}
The Payer Object
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Example Response
{% endapi-method-response-example-description %}

```yaml
{
    "card_id": "CV-af85ddba-f5f4-4644-b3fa-3c922e0687e9",
    "holder_name": "Thiago Gabriel",
    "expiration_month": 10,
    "expiration_year": 2040,
    "last4": "1111",
    "brand": "VI"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Example Error Response.
{% endapi-method-response-example-description %}

```yaml
{
    “code” : 5001,
    “message” : "Invalid parameter",
    “param” : "card.number"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## The Card Object

| **Argument** | **Type** | **Description** |
| :--- | :--- | :--- |
| `holder_name` | String | Cardholder's full name. **Required if** `token` **not present.** |
| `expiration_month` | Integer | Number representing the card's expiration month \(start in 1\). **Required if** `token` **not present.** |
| `expiration_year` | Integer | Number representing the card's expiration year. **Required if** `token` **not present.** |
| `number` | String | The card number, as a string without any separators. **Required if** `encrypted_data` **or** `token` **not present.** |
| `cvv` | String | Credit card verification value. **Required if** `encrypted_data` **or** `token` **not present.** |
| `encrypted_data` | String | [JWE](https://tools.ietf.org/html/rfc7516) encrypted params. Optional. |
| `token` | String | Temporary credit card token created using Smart Fields. Optional. |

## The Payer Object

| **Argument** | **Type** | **Description** |
| :--- | :--- | :--- |
| `name` | String | Payer's name. **Required.** |
| `document` | String | Payer's document. **Required.** |
| `email` | String | Payer's email address. Optional. |

### Example Request

```bash
curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Content-Type: application/json' \
    -H 'X-Version: 2.1' \
    -H 'User-Agent: MerchantTest / 1.0 ' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/secure_cards
```

**Example request body**

```yaml
{
    "country": "BR",
    "card": {
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "number": "4111111111111111",
        "cvv": "123"
    },
    "payer": {
        "name": "Luis Gabriel",
        "document": "53033315550",
        "email": "luis@email.com"
    }
}
```

{% api-method method="get" host=" https://api.dlocal.com/cards/" path="{card\_id}" %}
{% api-method-summary %}
Retrieve a Card
{% endapi-method-summary %}

{% api-method-description %}
Retrieve information about a saved card.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="card\_id" type="string" required=true %}
The card id received when saving the card.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
    "card_id": "CV-af85ddba-f5f4-4644-b3fa-3c922e0687e9",
    "holder_name": "Thiago Gabriel",
    "expiration_month": 10,
    "expiration_year": 2040,
    "last4": "1111",
    "brand": "VI"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Example Request

```bash
curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Content-Type: application/json' \
    -H 'X-Version: 2.1' \
    -H 'User-Agent: MerchantTest / 1.0 ' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/secure_cards
```

{% api-method method="delete" host=" https://api.dlocal.com/secure\_cards/" path="{card\_id}" %}
{% api-method-summary %}
Delete a card
{% endapi-method-summary %}

{% api-method-description %}
Unlink a `card_id` so that it cannot be use any further.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="card\_id" type="string" required=false %}
The card id received when saving the card
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
    "card_id" : "CV-af85ddba-f5f4-4644-b3fa-3c922e0687e9",
     "deleted" : true 
}

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Example Request

```bash
curl -X DELETE \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Content-Type: application/json' \
    -H 'X-Version: 2.1' \
    -H 'User-Agent: MerchantTest / 1.0 ' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/secure_cards/CV-af85ddba-f5f4-4644-b3fa-3c922e0687e9
```

## Http Errors

| **HTTP Status Code** | **Error Code** | **Error Detail** |
| :--- | :--- | :--- |
| `403 Forbidden` | 3001 | Invalid Credentials. |
| ​ | 3002 | Unregistered IP address. |
| ​ | 3003 | Merchant has no authorization to use this API. |
| `400 Bad Request` | 5000 | Invalid request. |
| ​ | 5001 | Invalid parameter. |
| ​ | 5003 | Country not supported. |
| ​ | 5005 | User unauthorized due to cadastral situation. |
| ​ | 5008 | Token not found or inactive. |
|  | 5015 | The card was rejected by the bank. |



