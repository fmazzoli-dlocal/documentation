# Security

#### Signature <a id="signature"></a>

The signature should use SHA256 as HMAC hash function. The signature header always should have the version prefix that contains the signature version and the used hash function. For now, V2-HMAC-SHA256.

#### Headers <a id="headers"></a>

| **Header** | **Type** | **Description** |
| :--- | :--- | :--- |
| `X-Date` | String | ISO8601 Datetime with Timezone. Eg `2018-07-12T13:46:28.629Z` |
| `X-Login` | String | Merchant xLogin |
| `X-Trans-Key` | String | Merchant xTransKey |
| `Content-Type` | String | `application/json` |
| `X-Version` | String | API Version |
| `User-Agent` | String | Used to identify the application type, operating system, software vendor or software version of the requesting software user agent. |
| Authorization | String | &lt;auth version&gt;, Signature: &lt;hmac\(secretKey, "X-Login+X-Date+RequestBody"\)&gt; |

#### Examples of HMAC signature generation in the most popular languages

{% tabs %}
{% tab title="Java" %}
```java
import java.io.ByteArrayOutputStream;
import java.io.IOException;
import java.security.InvalidKeyException;
import java.security.NoSuchAlgorithmException;
import java.util.Formatter;
import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;

public final class SignatureCalculator {

    private static final String HMAC_ALGORITHM = "HmacSHA256";
    private static final String CHARSET = "UTF-8";

    public static String calculateSignature(String x_Login, String x_Date, String secretKey, String body)
        throws IOException, InvalidKeyException, NoSuchAlgorithmException {

        // Create byte array with the required data for the signature.
        ByteArrayOutputStream bout = new ByteArrayOutputStream();
        bout.write(x_Login.getBytes(CHARSET));
        bout.write(x_Date.getBytes(CHARSET));
        bout.write(body.getBytes(CHARSET));

        // Calculate the signature.
        SecretKeySpec signingKey = new SecretKeySpec(secretKey.getBytes(), HMAC_ALGORITHM);
        Mac mac = Mac.getInstance(HMAC_ALGORITHM);
        mac.init(signingKey);
        byte[] signature = mac.doFinal(bout.toByteArray());

        // Create a String with the signature value.
        Formatter formatter = new Formatter();
        for (byte b : signature) {
            formatter.format("%02x", b);
        }
        return formatter.toString();
    }
}
```
{% endtab %}

{% tab title="Other Languages" %}
| Language | Code |
| :--- | :--- |
| PHP | `$signature = hash_hmac("sha256", "$X-Login$X-Date$RequestBody", $secretKey);` |
| Python | `signature = hmac.new(secretKey, X-Login+X-Date+RequestBody, hashlib.sha256).hexdigest()` |
| Ruby | `signature = OpenSSL::HMAC.hexdigest('sha256', secretKey, $X-Login + $X-Date + RequestBody)` |
{% endtab %}
{% endtabs %}

### Sensitive data encryption <a id="sensitive-data-encryption"></a>

Credit Card data, such as `number` and `cvv`, can be encrypted inside the JSON Request Body using [JWE](https://tools.ietf.org/html/rfc7516). This standard is being widely used in the market, and [most programming languages have libraries](https://openid.net/developers/jwt/) to support it.

The following parameters can be encrypted and added to a  `encrypted_data` field:

{% tabs %}
{% tab title="Properties" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `cvv` | String | Credit Card security code |
| `number` | String | Credit Card number |
{% endtab %}

{% tab title="Example Credit Card Encrypted Body" %}
```yaml
"card": {
    "holder_name": "Thiago Gabriel",
    "expiration_month": 10,
    "expiration_year": 2040,
    "encrypted_data": "[encrypted JSON goes here]"
}
```
{% endtab %}
{% endtabs %}

The encryption flow is the following

1. dLocal creates an RSA key pair and issue a certification with a 3rd party authority.
2. dLocal shares the public key to the merchant using an encrypted method. _Ask your Technical Account Manager for more information_.
3. The merchant uses this public key to encrypt the `number` and `cvv` into a JSON using JWE, and send it in the API request within the `encrypted_data` field. The rest of the request can be sent unencrypted.
4. dLocal decrypts the message using the private key. 

## Idempotent Requests <a id="idempotent-requests"></a>

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
    -H 'Content-Type: application/json' \
    -H 'X-Version: 2.1' \
    -H 'User-Agent: MerchantTest / 1.0 ' \
    -H 'X-Idempotency-Key: a8a85bce-5733-4a6c-91b5-553ed4b3de16' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    -d '{body}'
    https://api.dlocal.com/payments
```

