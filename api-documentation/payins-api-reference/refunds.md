# Refunds

This service allows you to create and read refunds of an existing payment.

A Refund is the reversal of a credit card [payment](payments.md#create-a-payment), where the funds are taken from the Merchant and given back to the Card Holder. A refund processing fee may apply.

{% api-method method="post" host=" https://api.dlocal.com/" path="refunds" %}
{% api-method-summary %}
Make a Refund
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="order\_refund\_id" type="string" required=false %}
Refund id given by the merchant in their system.
{% endapi-method-parameter %}

{% api-method-parameter name="id\_payment" type="string" required=true %}
The payment id
{% endapi-method-parameter %}

{% api-method-parameter name="notification\_url" type="string" required=true %}
If a refund is pending, the refund confirmation is sent asynchronously to this URL.
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="number" required=false %}
Amount to refund. If the amount is empty, then the default is total amount of the payment.
{% endapi-method-parameter %}

{% api-method-parameter name="currency" type="string" required=false %}
Currency of the Amount.  
**Required if** `amount` **is present.**
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
Description of the refund.
{% endapi-method-parameter %}

{% api-method-parameter name="beneficiary\_name" type="string" required=false %}
User's full name.  
**Required if the** `type` **of the payment is** `TICKET` **or** `BANK_TRANSFER` **.**
{% endapi-method-parameter %}

{% api-method-parameter name="bank" type="string" required=false %}
User's bank name.  
**Required if the** `type` **of the payment is** `TICKET` **or** `BANK_TRANSFER` **.**
{% endapi-method-parameter %}

{% api-method-parameter name="bank\_account" type="string" required=false %}
User's bank account number.  
**Required if the** `type` **of the payment is** `TICKET` **or** `BANK_TRANSFER` **.**
{% endapi-method-parameter %}

{% api-method-parameter name="bank\_account\_type" type="string" required=false %}
Type of bank account. `C`: for Current accounts; `S`: for Savings accounts; `I`: International accounts.  
**Required if the** `type` **of the payment is** `TICKET` **or** `BANK_TRANSFER` **.**
{% endapi-method-parameter %}

{% api-method-parameter name="bank\_branch" type="string" required=false %}
User's bank branch name.  
**Required if the** `type` **of the payment is** `TICKET` **or** `BANK_TRANSFER` **.**
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "id" : "REF42342",
   "id_payment" : "PAY4334346343",
   "order_refund_id" : "7625347623",
   "notification_url" : "http://some.url",
   "amount" : 803.04,
   "currency" : "BRL",
   "status" : "SUCCESS",
   "status_code" : 200,
   "status_detail" : "The refund was paid",
   "created_date" : "2018-09-06T22:03:03.000+0000",
   "amount_refunded" : 803.04
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
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/refunds
```

#### Example Request Body

```yaml
{
    "id_payment" : "PAY4334346343",
    "order_refund_id" : "7625347623",
    "amount": 100.00,
    "currency": "USD",
    "notification_url": "http://some.url"
}
```

## Refund Asynchronous Notification

If a refund is pending, the refund confirmation is sent asynchronously to the refund notification URL by POST, sending the following parameters:

#### The Refund Object

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | String | The refund id. |
| `payment_id` | String | The payment id. |
| `order_refund_id` | String | The refund id given by the merchant in their system. |
| `amount` | Positive Float | The amount of the refund. |
| `amount_refunded` | Positive Float | The refunded amount. |
| `currency` | String | The currency code of the refund. |
| `status` | String | The status of the refund. |
| `status_code` | String | The [status](refunds.md#refund-status) code of the refund. |
| `status_detail` | String | The status detail. |
| `created_date` | String | The date of when the refund was executed. |
| `notification_URL` | String | URL where dlocal will send notifications associated to changes in this refund. |
| `description` | String | Description of the refund. |
| `bank` | String | User's bank name. |
| `bank_account` | String | User's bank account number. |
| `bank_account_type` | String | Type of bank account. `C`: for Current accounts; `S`: for Savings accounts; `I`: International accounts. |
| `bank_branch` | String | User's bank branch name. |

## Example POST

POST**:** _{refund.notification\_url}_

```yaml
{
    "id" : "REF42342",
    "payment_id" : "PAY245235",
    "order_refund_id" : "7625347623",
    "amount" : 100.00,
    "amount_refunded" : 100.00,
    "currency" : "USD",
    "status" : "SUCCESS",
    "status_code" : "200",
    "status_detail" : "The refund was paid.",
    "created_date" : "2018-02-15T15:14:52-00:00"
}
```

{% api-method method="get" host=" https://api.dlocal.com/refunds/" path="{id}" %}
{% api-method-summary %}
Retrieve a Refund
{% endapi-method-summary %}

{% api-method-description %}
Retrieve information about a refund.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The refund id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "id" : "REF42342",
   "id_payment" : "PAY4334346343",
   "order_refund_id" : "7625347623",
   "notification_url" : "http://some.url",
   "amount" : 803.04,
   "currency" : "BRL",
   "status" : "SUCCESS",
   "status_code" : 200,
   "status_detail" : "The refund was paid",
   "created_date" : "2018-09-06T22:03:03.000+0000",
   "amount_refunded" : 803.04
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Example Request

```bash
$ curl \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/refunds/REF42342
```

{% api-method method="get" host="https://api.dlocal.com/refunds/" path="{id}/status" %}
{% api-method-summary %}
Retrieve a Refund Status
{% endapi-method-summary %}

{% api-method-description %}
Retrieve information about the status of a refund.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The refund id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Example Response
{% endapi-method-response-example-description %}

```yaml
{
    "id": "REF42342",
    "status": "SUCCESS",
    "status_code": "200",
    "status_detail": "The refund was paid.",
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Refund Status Codes <a id="refund-status"></a>

| Status | Status code | Description |
| :--- | :--- | :--- |
| `PENDING` | 100 | The refund is pending. |
| `SUCCESS` | 200 | The refund was paid. |
| `REJECTED` | 300 | The refund was rejected. |
| `CANCELLED` | 400 | The refund was cancelled. |

