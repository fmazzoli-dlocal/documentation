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
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## The Card Object

| **Argument** | **Type** | **Description** |
| --- | --- | --- | --- | --- | --- | --- |
| `holder_name` | String **\(Required\)** | Cardholder's full name |
| `expiration_month` | Integer **\(Required only if** `token` **not present\)** | Number representing the card's expiration month \(start in 1\). |
| `expiration_year` | Integer **\(Required only if** `token` **not present\)** | Number representing the card's expiration year. |
| `number` | String **\(Required if** `encrypted_data` or `token` **not present\)** | The card number, as a string without any separators. |
| `cvv` | String **\(Required is** `encrypted_data` or `token` **not present\)** | Credit card verification value. |
| `encrypted_data` | String \(Optional\) | [JWE](https://tools.ietf.org/html/rfc7516) encrypted params. |
| `token` | String \(Optional\) | Temporary credit card token created using Smart Fields. |

## The Payer Object

| **Argument** | **Type** | **Description** |
| --- | --- | --- |
| `name` | String **\(Required\)** | Payer's name |
| `document` | String **\(Required\)** | Payer's document |

## Example Request

```bash
curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
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
        "number": "41111111111111",
        "cvv": "123",
    },
    "payer": {
        "name": "Luis Gabriel",
        "document": "53033315550",
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

## Example request

```bash
$ curl \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/cards/CV-e90078f7-e027-4ce4-84cb-534c877be33c
```

