# Bank Transfer Payments

## Redirect Bank Transfer Payments

All Bank Transfer \(`BANK_TRANSFER`\) payment methods offer a redirect solution \(`payment_method_flow` = `REDIRECT`\). The API returns a `redirect_URL`, which is used to redirect the user to a dLocal-hosted page. The user will be able to see the details in order to complete the transfer via their home banking.

Using the Redirect method, the payment will have the `PENDING` status until the user completes the transfer, and dLocal gets notified.

The example below belongs to payment using Caixa in Brazil. For a full list of `BANK_TRANSFER` payment methods available, visit the [Payment Methods page](../payment-methods/).

{% tabs %}
{% tab title="Example Request" %}
#### Example Request <a id="example-request-3"></a>

```bash
curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/payments
```

#### Example Request Body <a id="example-request-body"></a>

```yaml
{
    "amount": 100,
    "currency": "BRL",
    "country": "BR",
    "payment_method_id": "CA",
    "payment_method_flow": "REDIRECT",
    "payer": {
        "name": "Thiago Gabriel",
        "email": "thiago@example.com",
        "document": "52463567015"
    },
    "order_id": "623576234",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}

{% tab title="Example Response" %}
#### Example Response

```yaml
{
    "id": "D-4-82f1d728-6966-41f8-8fea-fc9ee0e7cded",
    "amount": 100,
    "currency": "BRL",
    "payment_method_id": "CA",
    "payment_method_type": "BANK_TRANSFER",
    "payment_method_flow": "REDIRECT",
    "country": "BR",
    "created_date": "2018-12-26T21:19:02.000+0000",
    "status": "PENDING",
    "status_detail": "The payment is pending",
    "status_code": "100",
    "order_id": "623576234",
    "notification_url": "http://merchant.com/notifications",
    "redirect_url": "https://pay.dlocal.com/collect/pay/pay/M-de20ae10-0953-11e9-b88f-39144191f925?xtid=CATH-ST-1545859142-2123845504"
}
```
{% endtab %}
{% endtabs %}

![Example of redirect page of a Caixa bank transfer](../../../.gitbook/assets/image%20%2816%29.png)

