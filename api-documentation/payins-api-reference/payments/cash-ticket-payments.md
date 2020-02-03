# Cash \(Ticket\) Payments

## Redirect Cash Payments

All Cash \(`TICKET`\) payment methods offer a redirect solution \(`payment_method_flow` = `REDIRECT`\). The API returns a `redirect_URL`, which is used to redirect the user to a dLocal-hosted page. The user will be able to see the ticket in order to print it or pay using their home banking.

Using the Redirect method, the payment will have the `PENDING` status until the user pays the ticket, and dLocal gets notified.

The example below belongs to payment using OXXO in Mexico. For a full list of `TICKET` payment methods available, visit the [Payment Methods page](../payment-methods/).

{% tabs %}
{% tab title="Example Request" %}
#### Example Request <a id="example-request-3"></a>

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
    https://api.dlocal.com/payments
```

#### Example Request Body <a id="example-request-body"></a>

```yaml
{
    "amount": 100,
    "currency": "MXN",
    "country": "MX",
    "payment_method_id": "OX",
    "payment_method_flow": "REDIRECT",
    "payer": {
        "name": "Thiago Gabriel",
        "email": "thiago@example.com",
        "document": "53033315550"
    },
    "order_id": "5346523564",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}

{% tab title="Example Response" %}
#### Example Response

```yaml
{
    "id": "D-4-75c7473a-ab86-4e43-bd39-c840268747d3",
    "amount": 100,
    "currency": "MXN",
    "payment_method_id": "OX",
    "payment_method_type": "TICKET",
    "payment_method_flow": "REDIRECT",
    "country": "MX",
    "created_date": "2018-12-26T20:37:20.000+0000",
    "status": "PENDING",
    "status_detail": "The payment is pending",
    "status_code": "100",
    "order_id": "5346523564",
    "notification_url": "http://merchant.com/notifications",
    "redirect_url": "https://sandbox.dlocal.com/collect/pay/pay/M-0aa0cc00-094e-11e9-9f92-dbdad3ad0963?xtid=CATH-ST-1545856640-602791137"
}
```
{% endtab %}
{% endtabs %}

![Example of redirect page of a OXXO ticket ](../../../.gitbook/assets/image%20%2816%29.png)

## Direct Cash Payments

Some alternative payment methods are available via our **Direct APMs** solution \(`payment_method_flow` = `DIRECT`\). The important parameters of a ticket are returned via API, so the merchant can build their own UI.

The example below belongs to direct payment using Boleto Bancário in Brazil. For a full list of `TICKET` payment methods available, visit the [Payment Methods page](../payment-methods/).

{% tabs %}
{% tab title="Example Request" %}
#### Example Request <a id="example-request-3"></a>

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
    https://api.dlocal.com/payments
```

#### Example Request Body <a id="example-request-body"></a>

```yaml
{
    "amount": 120,
    "currency": "USD",
    "country": "BR",
    "payment_method_id": "BL",
    "payment_method_flow": "DIRECT",
    "payer": {
        "name": "Thiago Gabriel",
        "email": "thiago@example.com",
        "document": "53033315550",
        "user_reference": "12345",
        "address": {
            "state": "Rio de Janeiro",
            "city": "Volta Redonda",
            "zip_code": "27275-595",
            "street": "Servidao B-1",
            "number": "1106"
        }
    },
    "order_id": "5346523564",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}

{% tab title="Example Response" %}
#### Example Response

```yaml
{
    "id": "D-4-965cbd38-92d4-4e71-a000-2f653d7d16c6",
    "amount": 120,
    "currency": "USD",
    "payment_method_id": "BL",
    "payment_method_type": "TICKET",
    "payment_method_flow": "DIRECT",
    "country": "BR",
    "ticket": {
        "type": "CUSTOM",
        "number": "34191090080056880044554689940002877570000096000",
        "expiration_date": "2019-01-03T01:59:00.000+0000",
        "id": "109/00005688-0",
        "barcode": "34198775700000960001090000568800445468994000",
        "company_name": "DLOCAL BRASIL LTDA",
        "provider_name": "itau",
        "provider_logo": "http://static-sandbox.dlocal.com/images/providers/itau.png",
        "image_url": "http://backoffice.dlocal.sandbox/gmf/payments/M-146aa2f0-094f-11e9-9f92-dbdad3ad0963"
    },
    "created_date": "2018-12-26T20:44:44.445+0000",
    "status": "PENDING",
    "order_id": "5346523564",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}

![Example mobile UI built with the information in the example above](../../../.gitbook/assets/image%20%288%29.png)

### The Ticket Object

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `type` | String | Type of ticket, can be `NUMERIC`, `BARCODE` or `CUSTOM` |
| `number` | String | Numeric code of the `NUMERIC` or `CUSTOM` ticket |
| `barcode` | String | Code to be included in the barcode of the `BARCODE` or `CUSTOM` ticket. |
| `format` | String | Format of the barcode of the `BARCODE` or `CUSTOM` ticket. Example `CODE_128,`or `ITF` |
| `id` | String | Reference code of the ticket |
| `expiration_date` | Date\(ISO-8601\) | The expiration date of the ticket. |
| `company_name` | String | Name of the company that acts as the beneficiary of the payment.  |
| `company_id` | String | Identifier of the company. |
| `provider_name` | String | Name of the company/bank that is creating the ticket. |
| `provider_logo` | String | URL of the logo of the company/bank that is creating the ticket. |
| `image_url` | String | URL of the full version of the ticket.  |

