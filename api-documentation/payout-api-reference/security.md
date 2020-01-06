# Security

All requests to the payouts API must be signed and the signature appended to the **Payload-Signature** request header for them to be accepted.

The signature must be calculated using the **request payload** as the data to be hashed and the merchant **secret key** as the hashing key, using the algorithm HMAC SHA256. The resulting signature should be provided in hexadecimal lowercase format.

The following PHP code snippet describes an example signature calculation:

### **Signature calculation example**

```text
$secretKey = 'xxxxxxxxxxx';
$requestPayload = { … }
$signature = hash_hmac('sha256', $requestPayload, $secretKey, false)
```

{% hint style="info" %}
You can find your **secret key** in the [Merchant Panel](https://merchant.dlocal.com/panel), under the Integration &gt; Credentials & Settings section.
{% endhint %}



