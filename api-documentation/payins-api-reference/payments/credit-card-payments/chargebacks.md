# Chargebacks

## Chargeback asynchronous notification

If a chargeback was applied \(requested by the user\) a notification is sent to the previously registered Merchant chargeback notification URL by POST protocol, sending the following parameters:

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | String | The chargeback id. |
| `payment_id` | String | The payment id. |
| `amount` | Positive Float | The amount of the chargeback. |
| `currency` | String | The currency of the chargeback. |
| `status` | String | The [status](chargebacks.md#chargeback-status) of the chargeback. |
| `status_code` | String | The status code of the chargeback. |
| `status_detail` | String | The description of the chargeback's status. |
| `created_date` | String | The date of when the chargeback was executed. |

{% hint style="info" %}
Chargeback notifications are signed. [Learn more about the signature notifications here.](../#signature-of-notifications)
{% endhint %}

**Example post**

POST: _{merchant.chargeback\_url}_

```yaml
{
    "id": "CHAR42342",
    "payment_id": "PAY245235",
    "amount": 100.00,
    "currency": "USD",
    "status": "COMPLETED",
    "status_code": "200",
    "status_detail": "The chargeback was executed.",
    "created_date" : "2018-02-15T15:14:52-00:00"
}
```

{% api-method method="get" host=" https://api.dlocal.com/chargebacks/" path="{chargeback\_id}" %}
{% api-method-summary %}
Retrieve a Chargeback
{% endapi-method-summary %}

{% api-method-description %}
Retrieve information about a chargeback.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="chargeback\_id" type="string" required=true %}
The chargeback id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
    "id": "CHAR42342",
    "payment_id": "PAY245235",
    "amount": 100.00,
    "currency": "USD",
    "status": "COMPLETED",
    "status_code": "200",
    "status_detail": "The chargeback was executed.",
    "created_date" : "2018-02-15T15:14:52-00:00"
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
    -H 'X-Version: 2.1' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/chargebacks/CHAR42342
```

{% api-method method="get" host="https://api.dlocal.com/chargebacks/" path="{chargeback\_id}/status" %}
{% api-method-summary %}
Retrieve a Chargeback Status
{% endapi-method-summary %}

{% api-method-description %}
Retrieve information about the status of a chargeback.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="chargeback\_id" type="string" required=true %}
The chargeback id
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
    "id": "CHAR42342",
    "status": "COMPLETED",
    "status_code": "200",
    "status_detail": "The chargeback was executed."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Chargeback status <a id="chargeback-status"></a>

| **Status** | **Status code** | **Description** |
| :--- | :--- | :--- |
| `PENDING` | 100 | The chargeback is pending. |
| `COMPLETED` | 200 | The chargeback was executed. |
| `CANCELLED` | 400 | The chargeback was cancelled. |

In the Production environment, Chargebacks are triggered by the buyer by calling their bank. In dLocal's Sandbox environment though, merchants can simulate a Chargeback using the method described below:

{% api-method method="post" host="https://sandbox.dlocal.com" path="/sandbox-tools/chargebacks" %}
{% api-method-summary %}
Simulate Chargeback \(Sandbox only\)
{% endapi-method-summary %}

{% api-method-description %}
Simulate a Chargeback in Sandbox
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="payment\_id" type="string" required=true %}
ID of the payment that is being chargebacked.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful response returns the id of the chargeback. 
{% endapi-method-response-example-description %}

```yaml
{
    "id": "CBK-4-184-45b0b9ae-4e05-419e-9248-d5890437b719"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Example Request

```bash
$ curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Content-Type: application/json' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://sandbox.dlocal.com/sandbox-tools/chargebacks
```

#### Example Request Body

```yaml
{
    "payment_id" : "PAY4334346343"
}
```

