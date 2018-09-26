# Security

#### Signature {#signature}

The signature should use SHA256 as HMAC hash function. The signature header always should have the version prefix that contains the signature version and the used hash function. For now, V2-HMAC-SHA256.

#### Headers {#headers}

| **Header** | **Type** | **Description** |
| :--- | :--- | :--- |
| `X-Date` | String | ISO8601 Datetime with Timezone. Eg `2018-07-12T13:46:28.629Z` |
| `X-Login` | String | Merchant xLogin |
| `X-Trans-Key` | String | Merchant xTransKey |
| Authorization | String | &lt;auth version&gt;, Signature: &lt;hmac\(secretKey, "X-Login+X-Date+RequestBody"\)&gt; |

### Sensitive data encryption {#sensitive-data-encryption}

Credit Card data, such as number and cvv, will be encrypted inside the Json Request Body using [JWE](https://tools.ietf.org/html/rfc7516). This standard is being widely used in the market, so most used languages have any libraries to support it, simplifying the integration for our merchants.

The following parameters can be encrypted and added to a new `encrypted_data` field:

{% tabs %}
{% tab title="Properties" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `cvv` | String | Credit Card security code |
| `number` | String | Credit Card number |
{% endtab %}

{% tab title="Example Credit Card Encrypted Body" %}
```yaml
{
    "holder_name": "Thiago Gabriel",
    "expiration_month": 10,
    "expiration_year": 2040,
    "encrypted_data": "eyJlbmMiOiJBMjU2R0NNIiwiYW..."
}
```
{% endtab %}
{% endtabs %}

## Idempotent Requests {#idempotent-requests}

To perform an idempotent request, provide an additional 'X-Idempotency-Key' header to the request.

| **Header** | **Type** | **Description** |
| :--- | :--- | :--- |
| `X-Idempotency-Key` | String | Key used for perform an idempotent request. Optional. |

#### Example Request

```bash
curl -X POST \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'X-Idempotency-Key: a8a85bce-5733-4a6c-91b5-553ed4b3de16' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/payments
```

