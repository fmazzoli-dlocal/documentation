---
description: Signature of message
---

# Security

All request to the payouts API must be signed using the merchant secret key with algorithm HMAC SHA256 in Hexadecimal lowercase format. 

The signature must be calculated using the request payload and adding this result in a request header with name Payload-Signature.

The following table describe an example calculation algorithm based on PHP language:

### **Signature calculation algorithm** 

```text
$secretKey = 'xxxxxxxxxxx';
$requestPayload = { … }
$signature = hash_hmac('sha256', $requestPayload, $secret, false)
```

