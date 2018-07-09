# Refunds

This service allows you to create and read refunds of an existing payment.

A Refund is the reversal of a credit card [payment](https://dlocal.com/docs/?language=cURL#create-a-payment), where the funds are taken from the Merchant and given back to the Card Holder. A refund processing fee may apply.

{% api-method method="post" host=" https://api.dlocal.com/" path="refunds" %}
{% api-method-summary %}
Make a Refund
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="id\_payment" type="string" required=true %}
The payment id
{% endapi-method-parameter %}

{% api-method-parameter name="notification\_url" type="string" required=true %}
If a refund is pending, the refund confirmation is sent asynchronously to this URL.
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="string" required=false %}
Amount to refund. Default is total amount of the payment.
{% endapi-method-parameter %}

{% api-method-parameter name="currency" type="string" required=true %}
Currency of the Amount. **Only required if `amount` is present.**
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
    "id": "REF42342",
    "id_payment": "PAY4334346343",
    "amount": 100.00,
    "amount_refunded": 100.00,
    "currency": "USD",
    "status": "SUCCESS",
    "status_detail": "The refund was paid.",
    "notification_url": "http://some.url",
    "created_date" : "2018-02-15T15:14:52-00:00"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Example Request

```bash
$ curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/refunds
```

### Example Request Body

```yaml
{
    "id_payment" : "PAY4334346343",
    "amount": 100.00,
    "currency": "USD",
    "notification_url": "http://some.url"
}
```

## Refund Asynchronous Notification

If a refund is pending, the refund confirmation is sent asynchronously to the refund notification URL by POST, sending the following parameters:

| Property | Type | Description |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `id` | String | The refund id. |
| `payment_id` | String | The payment id. |
| `amount` | Positive Float | The amount of the refund. |
| `amount_refunded` | Positive Float | The refunded amount. |
| `currency` | String | The currency code of the refund. |
| `status` | String | The status of the refund. |
| `status_code` | Integer | The [status](https://dlocal.com/docs/?language=cURL#refund-status) code of the refund. |
| `created_date` | String | The date of when the refund was executed. |

## Example POST

POST**:** _{refund.notification\_url}_

```yaml
{
    "id": "REF42342",
    "payment_id": "PAY245235",
    "amount": 100.00,
    "amount_refunded": 100.00,
    "currency": "USD",
    "status": "SUCCESS",
    "status_code": 200,
    "created_date" : "2018-02-15T15:14:52-00:00"
}
```

## Refund Status Codes {#refund-status}

| Status | Status code | Description |
| --- | --- | --- | --- | --- |
| `PENDING` | 100 | The refund is pending. |
| `SUCCESS` | 200 | The refund was paid. |
| `REJECTED` | 300 | The refund was rejected. |
| `CANCELLED` | 400 | The refund was cancelled. |
