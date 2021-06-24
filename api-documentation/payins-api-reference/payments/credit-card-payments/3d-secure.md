# 3D-Secure

## Redirect 3D-Secure

{% hint style="warning" %}
Redirect 3D-Secure is mandatory in: India, South Africa, the Philippines and Debit cards in Brazil. 
{% endhint %}

In some regions 3D-Secure authentication might be mandatory. In such a scenario, the [Create a Payment](https://docs.dlocal.com/api-documentation/payins-api-reference/payments#create-a-payment) function will return a payment with `status` =`PENDING` \(`status_code` = `101` \). The Payment Object in the response will include a 3D-Secure object \(`three_dsecure`\), containing the `redirect_url` that the user needs to be redirected to so as to complete the authorization.

Once the user completed the authentication successfully, the payment will be processed and the user will be redirected to the `callback_url` .

### Example Authorization with Redirect

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
    https://api.dlocal.com/secure_payments
```

#### Example Request Body <a id="example-request-body"></a>

```yaml
{
    "amount": 120.00,
    "currency" : "BRL",
    "country": "BR",
    "payment_method_id" : "CARD",
    "payment_method_flow" : "DIRECT",
    "payer":{
        "name" : "Thiago Gabriel",
        "email" : "thiago@example.com",
        "document" : "53033315550",
        "user_reference": "12345",
        "address": {
            "state"  : "Rio de Janeiro",
            "city" : "Volta Redonda",
            "zip_code" : "27275-595",
            "street" : "Servidao B-1",
            "number" : "1106"
        },
        "ip" : "179.27.83.210",
        "device_id" : "2fg3d4gf234"
    },
    "card":{
        "holder_name" : "Thiago Gabriel",
        "number" : "4111111111111111",
        "cvv" : "123",
        "expiration_month" : 10,
        "expiration_year" : 2040,
        "capture" : false
    },
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications",
    "callback_url": "http://merchant.com/callback"
}
```
{% endtab %}

{% tab title="Example Response" %}
```yaml

    "id": "D-4-cf8eef6b-52d5-4320-b5ea-f5e0bbe4343f",
    "amount": 120,
    "currency": "BRL",
    "payment_method_id": "CARD",
    "payment_method_type": "CARD",
    "payment_method_flow": "DIRECT",
    "country": "BR",
    "card": {
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "brand": "VI",
        "last4": "1111"
    },
    "three_dsecure" : {
        "redirect_url" : "http://api.dlocal.com/three-ds/M-64356345634587b3495"
    },
    "created_date": "2018-12-26T20:26:09.000+0000",
    "status": "PENDING",
    "status_detail": "The payment is pending 3D Secure authentication.",
    "status_code": "101",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}

## 3rd-party Authentication \(MPI\)

{% hint style="warning" %}
3rd-party Authentication is only available in Brazil, Panama, Costa Rica, Guatemala and Nigeria at the moment.
{% endhint %}

Submit a payment, using authentication data from a third-party 3D Secure 1.0 provider.

To authorize a 3D-Secure authenticated payment, you need to include the `three_dsecure` object in your payment request.

### `three_dsecure` Object

{% tabs %}
{% tab title="three\_dsecure Object" %}
<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>mpi</code>
      </td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">
        <p><code>TRUE</code> if you are going to use a 3rd-party 3D Secure provider.</p>
        <p><b>If null, then <code>mpi</code> = <code>FALSE</code></b>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>three_dsecure_version</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>Note: At the moment only 3DS 1.0 is supported.</p>
        <p><b>If null, then <code>three_dsecure_version</code> = <code>&quot;1.0&quot;</code></b>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>cavv</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p></p>
        <p>The cardholder authentication value for the 3D Secure authentication session.
          The returned value is a base64-encoded 20-byte array.</p>
        <p><b>Required if <code>mpi</code> = <code>TRUE</code> and<code>three_dsecure_version</code> = <code>&quot;1.0&quot;</code></b>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>eci</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p></p>
        <p>The electronic commerce indicator.</p>
        <p><b>Required if <code>mpi</code> = <code>TRUE </code>and<code>three_dsecure_version</code> = <code>&quot;1.0&quot; </code></b>
        </p>
        <p>*See possible values and descriptions <a href="3d-secure.md#electronic-commerce-indicator-eci-values">here</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>xid</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p></p>
        <p>The transaction identifier assigned by the Directory Server (base64 encoded,
          20 bytes in a decoded form).</p>
        <p><b>Required if <code>mpi</code> = <code>TRUE </code>and<code>three_dsecure_version</code> = <code>&quot;1.0&quot;</code></b>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>enrollment_response</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p></p>
        <p>The enrollment response from the <code>VERes</code> message from the Directory
          Server.</p>
        <p>&quot;Y&quot;: Authentication available
          <br />&quot;N&quot; Cardholder not participating
          <br />&quot;U&quot;: Unable to authenticate/Card not eligible</p>
        <p><b>Optional</b>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>authentication_response</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p></p>
        <p>From the <code>PARes</code> from the issuer&apos;s Access Control System.</p>
        <p>&quot;Y&quot;: Authentication successful</p>
        <p>&quot;A&quot;: Attempts processing performed</p>
        <p>&quot;N&quot;: Authentication failed
          <br />&quot;U&quot;: Authentication could not be performed</p>
        <p><b>Optional</b>
        </p>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="Example three\_dsecure Object" %}
```yaml
"three_dsecure":{
    "mpi": true,
    "three_dsecure_version": "1.0",
    "cavv": "3q2+78r+ur7erb7vyv66vv\/\/\/\/8=",
    "eci": "05",
    "xid": "ODUzNTYzOTcwODU5NzY3Qw==",
    "enrollment_response": "Y"
    "authentication_response": "Y"
}
```
{% endtab %}
{% endtabs %}

### Example Authorization with 3rd-party Authentication

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
    https://api.dlocal.com/secure_payments
```

#### Example Request Body <a id="example-request-body"></a>

```yaml
{
    "amount": 120.00,
    "currency" : "BRL",
    "country": "BR",
    "payment_method_id" : "CARD",
    "payment_method_flow" : "DIRECT",
    "payer":{
        "name" : "Thiago Gabriel",
        "email" : "thiago@example.com",
        "document" : "53033315550",
        "user_reference": "12345",
        "address": {
            "state"  : "Rio de Janeiro",
            "city" : "Volta Redonda",
            "zip_code" : "27275-595",
            "street" : "Servidao B-1",
            "number" : "1106"
        },
        "ip" : "179.27.83.210",
        "device_id" : "2fg3d4gf234"
    },
    "card":{
        "holder_name" : "Thiago Gabriel",
        "number" : "4111111111111111",
        "cvv" : "123",
        "expiration_month" : 10,
        "expiration_year" : 2040,
        "capture" : false
    },
    "three_dsecure":{
        "mpi" : true,
        "three_dsecure_version" : "1.0",
        "cavv" : "3q2+78r+ur7erb7vyv66vv\/\/\/\/8=",
        "eci" : "05",
        "xid" : "ODUzNTYzOTcwODU5NzY3Qw==",
        "enrollment_response" : "Y",
        "authentication_response" : "Y"
    },
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}

{% tab title="Example Response" %}
```yaml
{
    "id": "D-4-cf8eef6b-52d5-4320-b5ea-f5e0bbe4343f",
    "amount": 120,
    "currency": "BRL",
    "payment_method_id": "CARD",
    "payment_method_type": "CARD",
    "payment_method_flow": "DIRECT",
    "country": "BR",
    "card": {
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "brand": "VI",
        "last4": "1111"
    },
    "three_dsecure": {
        "eci" : "05"
    },
    "created_date": "2018-12-26T20:26:09.000+0000",
    "approved_date": "2018-12-26T20:26:09.000+0000",
    "status": "AUTHORIZED",
    "status_detail": "The payment was authorized",
    "status_code": "600",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}

## Optional 3D-Secure

Submit a payment and choose whether you want to force the user to go through a 3D-Secure authentication.

To force a 3D-Secure authenticated payment, you need to create a payment with the parameter `force` = `TRUE` within the `three_dsecure` object.

{% hint style="warning" %}
Optional 3D-Secure  is available in Mexico, Turkey, Egypt, Nigeria, Dominican Republic, Indonesia, and Brazil \(For credit cards\).
{% endhint %}

### Example Authorization with Optional 3D-Secure 

{% tabs %}
{% tab title="Example Request" %}
#### Example Request

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
    https://api.dlocal.com/secure_payments
```

#### Example Request body

```yaml
{
    "amount": 120.00,
    "currency" : "BRL",
    "country": "BR",
    "payment_method_id" : "CARD",
    "payment_method_flow" : "DIRECT",
    "payer":{
        "name" : "Thiago Gabriel",
        "email" : "thiago@example.com",
        "document" : "53033315550",
        "user_reference": "12345",
        "address": {
            "state"  : "Rio de Janeiro",
            "city" : "Volta Redonda",
            "zip_code" : "27275-595",
            "street" : "Servidao B-1",
            "number" : "1106"
        },
        "ip" : "179.27.83.210",
        "device_id" : "2fg3d4gf234"
    },
    "card":{
        "holder_name" : "Thiago Gabriel",
        "number" : "4111111111111111",
        "cvv" : "123",
        "expiration_month" : 10,
        "expiration_year" : 2040,
    },
    "three_dsecure":{
        "force" : true,
    },
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}

{% tab title="Example Response" %}
```yaml
{
    "id": "D-4-cf8eef6b-52d5-4320-b5ea-f5e0bbe4343f",
    "amount": 120,
    "currency": "BRL",
    "payment_method_id": "CARD",
    "payment_method_type": "CARD",
    "payment_method_flow": "DIRECT",
    "country": "BR",
    "card": {
        "holder_name": "Thiago Gabriel",
        "expiration_month": 10,
        "expiration_year": 2040,
        "brand": "VI",
        "last4": "1111"
    },
    "three_dsecure" : {
        "redirect_url" : "http://api.dlocal.com/three-ds/M-64356345634587b3495"
    },
    "created_date": "2018-12-26T20:26:09.000+0000",
    "status": "PENDING",
    "status_detail": "The payment is pending 3D Secure authentication.",
    "status_code": "101",
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications"
}
```
{% endtab %}
{% endtabs %}



### Electronic Commerce Indicator \(ECI\) Values

| **`brand`** | **ECI** | **Description** |
| :--- | :--- | :--- |
| `VI`, `VD` | 05 | Authenticated by Issuer - Chargeback risk shifted to Issuer |
| `VI`, `VD` | 06 | Authenticated by Network - Chargeback risk shifted to Issuer |
| `VI`, `VD` | Other | Not authenticated |
| `MC`, `MD`, `MS` | 01 | Authenticated by Network - Chargeback risk shifted to Issuer |
| `MC`, `MD`, `MS` | 02 | Authenticated by Issuer - Chargeback risk shifted to Issuer |
| `MC`, `MD`, `MS` | 04 | Not authenticated |
| `MC`, `MD`, `MS` | Other | Not authenticated |
| `EL` | 05 | Authenticated by Issuer - Chargeback risk shifted to Issuer |
| `EL` | 06 | Authenticated by Network - Chargeback risk shifted to Issuer |
| `EL` | 07 | Not authenticated |

