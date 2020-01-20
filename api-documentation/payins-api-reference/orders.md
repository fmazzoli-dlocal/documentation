# Orders

Payments can include an `order_id` which is the ID of the payment given by the merchant in their system. Merchants can retrieve payments based on this ID.

## The Order Object

{% tabs %}
{% tab title="The Order Object" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `order_id` | String | ID given by the merchant in their system. |
| `payment_id` | String | The payment id at dLocal. |
| `amount` | Positive Float | Transaction amount \(in the currency entered in the field “currency”\). |
| `currency` | String | Three-letter [ISO currency code](https://www.iso.org/iso-4217-currency-codes.html), in uppercase. |
| `created_date` | Date \(ISO\_8601\) | Payment’s creation date. |
| `approved_date` | Date \(ISO\_8601\) | Payment’s approval date. |
| `status` | String | [Payment status](payments/#payment-status-codes). |
| `status_code` | String | The payment status code. |
| `status_detail` | String | Payment status detail. |
{% endtab %}

{% tab title="Order Object Example" %}
```yaml
{
    "order_id": "LDMYZ5mtmsCa",
    "payment_id": "D-4-f77392b1-4ff0-477c-749ac9a237b5",
    "currency": "USD",
    "amount": 382.00,
    "created_date": "2018-07-12T15:20:02.000+0000",
    "approved_date": "2018-07-12T15:20:02.000+0000",
    "status": "AUTHORIZED",
    "status_code": "600",
    "status_detail": "The payment was authorized."
}
```
{% endtab %}
{% endtabs %}

{% api-method method="get" host="https://api.dlocal.com/orders/" path="{order\_id}" %}
{% api-method-summary %}
Retrieve an Order
{% endapi-method-summary %}

{% api-method-description %}
Retrieve information about an existing order.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="order\_id" type="string" required=true %}
ID given by the merchant in their system.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
  "payment_id": "D-4-f77392b1-4ff0-477c-749ac9a237b5",
  "order_id": "LDMYZ5mtmsCa",
  "amount": 382.00,
  "currency": "USD",
  "approved_date": "2018-07-11T19:55:56.348Z",
  "created_date": "2018-07-11T19:55:56.348Z",
  "status": "PENDING",
  "status_code": "100",
  "status_detail": "The payment is pending"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Example Request

```bash
$ curl \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'X-Version: 2.1' \
    -H 'User-Agent: MerchantTest / 1.0 ' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/orders/43343463432
```

