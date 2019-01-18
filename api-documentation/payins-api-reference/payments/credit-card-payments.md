# Credit Card Payments

For credit card payments you can use the card information only if you business is [Full PCI DSS compliant](https://docs.dlocal.com/solutions/payins#pci-compliance). Otherwise you need to securely collect the card information using [Smart Fields](https://docs.dlocal.com/products/smart-fields).   
For recurring payments, first [save the card](https://docs.dlocal.com/api-documentation/payins-api-reference/saving-cards#create-a-card), and then use the `card_id` to charge the card.

{% hint style="info" %}
**Important**: If you are making a payment **with credit card information**, you need to use the following endpoint:   
h**ttps://api.dlocal.com/secure\_payments**

Card payments with a `card_id` or `token` should use the endpoint: **https://api.dlocal.com/payments**
{% endhint %}

## Payment with Credit Card information 

The following example applies for credit card payments using the plain credit card information \(**only for Full PCI DSS merchants**\). To make payments using encrypted card information, simply **replace** the `number`and `cvv`parameters with [`encrypted_data`](https://docs.dlocal.com/api-documentation/payins-api-reference/security#sensitive-data-encryption).

For card payments \(credit or debit\), you must send **`CARD`** as the `payment_method_id`.

{% tabs %}
{% tab title="Example Request" %}
#### Example Request <a id="example-request-3"></a>

```bash
curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'X-Content-Type: application/json' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/secure_payments
```

#### Example Request Body <a id="example-request-body"></a>

```yaml
{
    "amount": 120.00,
    "currency" : "USD",
    "country": "BR",
    "payment_method_id" : "CARD",
    "payment_method_flow" : "DIRECT",
    "payer":{
        "name" : "Thiago Gabriel",
        "email" : "thiago@example.com",
        "document" : "53033315550",
        "user_reference": "12345",
        "address": {
            "state"  : "Rio de Janeiro",
            "city" : "Volta Redonda",
            "zip_code" : "27275-595",
            "street" : "Servidao B-1",
            "number" : "1106"
        }
    },
    "card":{
        "holder_name" : "Thiago Gabriel",
        "number" : "4111111111111111",
        "cvv" : "123",
        "expiration_month" : 10,
        "expiration_year" : 2040
    },
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}

{% tab title="Example Response" %}
#### Example Response

```yaml
{
    "id": "D-4-cf8eef6b-52d5-4320-b5ea-f5e0bbe4343f",
    "amount": 120,
    "currency": "USD",
    "payment_method_id": "CARD",
    "payment_method_type": "CARD",
    "payment_method_flow": "DIRECT",
    "country": "BR",
    "card": {
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "brand": "VI",
        "last4": "1111"
    },
    "created_date": "2018-12-26T20:26:09.000+0000",
    "approved_date": "2018-12-26T20:26:09.000+0000",
    "status": "PAID",
    "status_detail": "The payment was paid",
    "status_code": "200",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}

## Payment with token from[ Smart Fields](../../../products/smart-fields/)

The following example applies for credit card payments using a [Smart Fields](../../../products/smart-fields/fields-setup-guide.md) `token`.

{% tabs %}
{% tab title="Example Request" %}
#### Example Request <a id="example-request-4"></a>

```bash
curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Content-Type: application/json' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/payments
```

#### Example Request Body <a id="example-request-body-1"></a>

```yaml
{
    "amount": 120.00,
    "currency" : "USD",
    "country": "BR",
    "payment_method_id" : "CARD",
    "payment_method_flow" : "DIRECT",
    "payer":{
        "name" : "Thiago Gabriel",
        "email" : "thiago@example.com",
        "document" : "53033315550",
        "user_reference": "12345",
        "address": {
            "state"  : "Rio de Janeiro",
            "city" : "Volta Redonda",
            "zip_code" : "27275-595",
            "street" : "Servidao B-1",
            "number" : "1106"
        }
    },
    "card":{
        "token": "CV-124c18a5-874d-4982-89d7-b9c256e647b5"
    },
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}

{% tab title="Example Response" %}
#### Example Response

```yaml
{
    "id": "D-4-80ca7fbd-67ad-444a-aa88-791ca4a0c2b2",
    "amount": 120,
    "currency": "USD",
    "payment_method_id": "CARD",
    "payment_method_type": "CARD",
    "payment_method_flow": "DIRECT",
    "country": "BR",
    "card": {
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "brand": "VI",
        "last4": "1111"
    },
    "created_date": "2018-12-26T20:28:47.000+0000",
    "approved_date": "2018-12-26T20:28:47.000+0000",
    "status": "PAID",
    "status_detail": "The payment was paid",
    "status_code": "200",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}

## Payment with `card_id` from [Create a Card](../saving-cards.md#create-a-card) method.

The following example applies for credit card payments using a the `card_id` gotten in the [Create a Card method.](../saving-cards.md#create-a-card)​​

{% tabs %}
{% tab title="Example Request" %}
#### Example Request <a id="example-request-4"></a>

```bash
curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Content-Type: application/json' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/payments
```

#### Example Request Body <a id="example-request-body-1"></a>

```yaml
{
    "amount": 120.00,
    "currency" : "USD",
    "country": "BR",
    "payment_method_id" : "CARD",
    "payment_method_flow" : "DIRECT",
    "payer":{
        "name" : "Thiago Gabriel",
        "email" : "thiago@example.com",
        "document" : "53033315550",
        "user_reference": "12345",
        "address": {
            "state"  : "Rio de Janeiro",
            "city" : "Volta Redonda",
            "zip_code" : "27275-595",
            "street" : "Servidao B-1",
            "number" : "1106"
        }
    },
    "card":{
        "card_id": "CID-124c18a5-874d-4982-89d7-b9c256e647b5"
    },
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}

{% tab title="Example Response" %}
#### Example Response​

```yaml
{
    "id": "D-4-80ca7fbd-67ad-444a-aa88-791ca4a0c2b2",
    "amount": 120,
    "currency": "USD",
    "payment_method_id": "CARD",
    "payment_method_type": "CARD",
    "payment_method_flow": "DIRECT",
    "country": "BR",
    "card": {
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "brand": "VI",
        "last4": "1111"
    },
    "created_date": "2018-12-26T20:28:47.000+0000",
    "approved_date": "2018-12-26T20:28:47.000+0000",
    "status": "PAID",
    "status_detail": "The payment was paid",
    "status_code": "200",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}



