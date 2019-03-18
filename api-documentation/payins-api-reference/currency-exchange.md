# Currency Exchange

## The Currency Exchange Object

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `from` | String | Origin currency code \(ISO-4217\) |
| `to` | String | Destination currency code \(ISO-4217\) |
| `rate` | Decimal | Ratio of conversion from `from` currency to `to` currency. |

{% api-method method="get" host="https://api.dlocal.com/currency-exchanges?" path="from={from}&to={to}" %}
{% api-method-summary %}
Get an Exchange Rate
{% endapi-method-summary %}

{% api-method-description %}
Get the exchange rate between two currencies.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="from" type="string" required=true %}
Origin currency code.
{% endapi-method-parameter %}

{% api-method-parameter name="to" type="string" required=true %}
Destination currency code.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Example Response
{% endapi-method-response-example-description %}

```yaml
{
    "from": "USD",
    "to": "BRL",
    "rate": 3.33
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
At the moment, only the only value for the `from` parameter is **`USD`**, and the `to`parameter can include any local currency.
{% endhint %}

## Example request

```bash
curl -X GET \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'X-Version: 2.1' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/currency-exchanges?from=USD&to=BRL
```

