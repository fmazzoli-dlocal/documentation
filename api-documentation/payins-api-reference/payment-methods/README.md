# Payment Methods

Object that identifies each payment method accepted by dLocal.

## The Payment Method Object

{% tabs %}
{% tab title="Payment Method Object" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | String | Payment method id |
| `type` | String | Type of method can be `CARD` `BANK_TRANSFER` `DIRECT_DEBIT` `TICKET`. |
| `name` | String | Payment type name |
| `countries` | String\[\] | Countries where the payment method is available. |
| `logo` | String | Payment method image url. |
| `allowed_flows` | String\[\] | Flows allowed for this payment, can be `DIRECT` or`REDIRECT`. |
{% endtab %}

{% tab title="Example Payment Method Object" %}
```yaml
{
  "id": "OX",
  "type": "TICKET",
  "name": "Oxxo",
  "countries" : ["MX"],
  "logo": "http://static.dlocal.com/payments-methods/OX/60x60",
  "allowed_flows": ["DIRECT", "REDIRECT"]
}
```
{% endtab %}
{% endtabs %}

{% api-method method="get" host=" https://api.dlocal.com/" path="payments-methods" %}
{% api-method-summary %}
Search Payment Methods
{% endapi-method-summary %}

{% api-method-description %}
This function returns a list of valid payment methods for the requested country.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="X-Date" type="string" required=true %}
ISO8601 Datetime with TimeZone.
{% endapi-method-parameter %}

{% api-method-parameter name="X-Login" type="string" required=true %}
Merchant xLogin
{% endapi-method-parameter %}

{% api-method-parameter name="X-Trans-Key" type="string" required=true %}
Merchant xTransKey
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
&lt;auth version&gt;, Signature: &lt;hmac\(secretKey, "X-Login+X-Date Header+RequestBody"\)&gt;
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="country" type="string" required=true %}
Payment method country code. See all country codes here.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
  {
      "id": "VI",
      "type": "CARD",
      "name": "Visa credit card",
      "logo": "http://static.dlocal.com/payments-methods/VI/60x60.png",
      "allowed_flows": ["DIRECT", "REDIRECT"]
  },
  {
      "id": "AE",
      "type": "CARD",
      "name": "American Express",
      "logo": "http://static.dlocal.com/payments-methods/AE/60x60.png",
      "allowed_flows": ["DIRECT", "REDIRECT"]
  },
  {
      "id": "GL",
      "type": "BANK_TRANSFER",
      "name": "Banco Galicia",
      "logo": "http://static.dlocal.com/payments-methods/BT/60x60.png",
      "allowed_flows": ["REDIRECT"]
  },
  {
      "id": "RP",
      "type": "TICKET",
      "name": "Rapi pago",
      "logo": "http://static.dlocal.com/payments-methods/RP/60x60.png",
      "allowed_flows": ["REDIRECT"]
  }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Example Request

```bash
curl -X GET \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/payments-methods?country=AR
```

## Payment Method Codes

To make **credit/debit card** [**payments**](../payments/#create-a-payment), you should use`"CARD"` as the `payment_method_id`.  
For **other types of payments** \(eg: bank transfer\), you should use the corresponding `payment_method_id`found in the country-specific pages below.

Examples:

* Payment with Visa credit card in Argentina, use `payment_method_id = "CARD"`  
* Payment with Rapi Pago in Argentina, use `payment_method_id = "RP"`

### **Payment Methods By Country**

* \*\*\*\*[**Argentina**](argentina.md#payment-methods-available)\*\*\*\*
* \*\*\*\*[**Brazil**](brazil.md#payment-methods-available)\*\*\*\*
* \*\*\*\*[**Chile**](chile.md#payment-methods-available)\*\*\*\*
* \*\*\*\*[**China**](chile.md#payment-methods-available)\*\*\*\*
* \*\*\*\*[**Colombia**](colombia.md#payment-methods-available)\*\*\*\*
* \*\*\*\*[**India**](india.md#payment-methods-available)\*\*\*\*
* \*\*\*\*[**Mexico**](mexico.md#payment-methods-available)\*\*\*\*
* \*\*\*\*[**Morocco**](morocco.md#payment-methods-available)\*\*\*\*
* \*\*\*\*[**Paraguay**](paraguay.md#payment-methods-available)\*\*\*\*
* \*\*\*\*[**Peru**](peru.md#payment-methods-available)\*\*\*\*
* \*\*\*\*[**Turkey**](turkey.md#payment-methods-available)\*\*\*\*
* \*\*\*\*[**Uruguay**](uruguay.md#payment-methods-available)\*\*\*\*

