# Refunds

This service allows you to create and read refunds of an existing payment.

A Refund is the reversal of a credit card [payment](payments/#create-a-payment), where the funds are taken from the Merchant and given back to the Card Holder. A refund processing fee may apply.

{% api-method method="post" host=" https://api.dlocal.com/" path="refunds" %}
{% api-method-summary %}
Make a Refund
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="payment\_id" type="string" required=true %}
The payment id
{% endapi-method-parameter %}

{% api-method-parameter name="notification\_url" type="string" required=true %}
If a refund is pending, the refund confirmation is sent asynchronously to this URL.
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="number" required=false %}
Amount to refund. If the amount is empty, then the default is total amount of the payment.  
**Required if** `currency` **is present.**
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
**Recommended if the** `type` **of the payment is** `TICKET` **or** `BANK_TRANSFER` **.**
{% endapi-method-parameter %}

{% api-method-parameter name="bank" type="string" required=false %}
User's bank name.  
**Recommended if the** `type` **of the payment is** `TICKET` **or** `BANK_TRANSFER` **.**
{% endapi-method-parameter %}

{% api-method-parameter name="bank\_account" type="string" required=false %}
User's bank account number.  
**Recommended if the** `type` **of the payment is** `TICKET` **or** `BANK_TRANSFER` **.**
{% endapi-method-parameter %}

{% api-method-parameter name="bank\_account\_type" type="string" required=false %}
Type of bank account. `C`: for Current accounts; `S`: for Savings accounts; `I`: International accounts.  
**Recommended if the** `type` **of the payment is** `TICKET` **or** `BANK_TRANSFER` **.**
{% endapi-method-parameter %}

{% api-method-parameter name="bank\_branch" type="string" required=false %}
User's bank branch name.  
**Recommended if the** `type` **of the payment is** `TICKET` **or** `BANK_TRANSFER` **.**
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
   "payment_id" : "PAY4334346343",
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

{% hint style="warning" %}
If any of the following parameters are missing or invalid, dLocal will send an email to the buyer \(to the email provided during the Create a Payment\) asking them for the information. 

Parameters: **`beneficiary_name` ,`bank` , `bank_account` , `bank_account_type` , `bank_branch`**
{% endhint %}

## Example Request

```bash
$ curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Content-Type: application/json' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/refunds
```

### Example Request Body

```yaml
{
    "payment_id" : "PAY4334346343",
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
    "amount" : 100.00,
    "amount_refunded" : 100.00,
    "currency" : "USD",
    "status" : "SUCCESS",
    "status_code" : "200",
    "status_detail" : "The refund was paid.",
    "created_date" : "2018-02-15T15:14:52-00:00"
}
```

{% api-method method="get" host=" https://api.dlocal.com/refunds/" path="{refund\_id}" %}
{% api-method-summary %}
Retrieve a Refund
{% endapi-method-summary %}

{% api-method-description %}
Retrieve information about a refund.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="refund\_id" type="string" required=true %}
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
   "payment_id" : "PAY4334346343",
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

{% api-method method="get" host="https://api.dlocal.com/refunds/" path="{refund\_id}/status" %}
{% api-method-summary %}
Retrieve a Refund Status
{% endapi-method-summary %}

{% api-method-description %}
Retrieve information about the status of a refund.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="refund\_id" type="string" required=true %}
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

### Errors

All the errors are returned with appropriate HTTP status code, 4XX or 5XX. The format of all errors is:

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `code` | Integer | Error code. |
| `message` | String | Human readable message. |
| `param` | String | In case one parameter is wrong. |

**Example error**

```yaml
{
    "code": 5012,
    "message": "Insufficient funds."
}
```

#### Http Errors <a id="http-errors"></a>

| **HTTP Status Code** | **Error Code** | **Error Detail** |
| :--- | :--- | :--- |
| `403 Forbidden` | 3001 | Invalid Credentials. |
|  | 3002 | Unregistered IP address. |
|  | 3003 | Merchant has no authorization to use this API. |
| `404 Not Found` | 4000 | Payment not found. |
| `400 Bad Request` | 5000 | Invalid request. |
|  | 5001 | Invalid parameter: \[parameter\_name\] |
|  | 5002 | Invalid transaction status. |
|  | 5003 | Country not supported. |
|  | 5004 | Currency not allowed for this country. |
|  | 5005 | User unauthorized due to cadastral situation. |
|  | 5006 | User limit exceeded. |
|  | 5007 | Amount exceeded. |
|  | 5010 | Request timeout. |
|  | 5011 | Order refund id is duplicated. |
|  | 5012 | Insufficient funds. |
|  | 5017 | Invalid API Version |
| `429 Too many requests` | 6000 | Too many requests to the API. |
| `500 Internal Server Error` | 7000 | The input is correct, but dLocal fails to process the payment. Rare case. |

