# Wallet Payments

Wallet payments \(`WALLET`\) ****require the user to log in to their wallet provider \(through a redirect\) and approve the payment. Once the first payment is successful, a token is returned which can be used to make recurring payments without the need of a redirect.

#### Redirect Wallet Payment

In this flow, the user is redirected to the wallet's website to authenticate. Once that's done, the user will be redirected back to the callback\_url, and the payment will be processed asynchronously. If wallet.save = `TRUE` in the request, the asynchronous notification will include a wallet.token , which can be used for further payments without the need to authenticating again.  


{% tabs %}
{% tab title="Example Request" %}
Example Request

```yaml
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

#### Example request body

```yaml
{
   "amount": 0,
   "currency": "ARS",
   "country": "AR",
   "payment_method_id": "MP",
   "payment_method_flow": "REDIRECT",
   "payer": {
       "name": "Thiago Gabriel",
       "email": "thiago@example.com",
       "document": "53033315550"
   },
   "wallet": {
       "save": TRUE,
       "verify": TRUE,
       "label": "New suscription for merchant service",
   },
   "description": "Exclusive contents with this service",   
   "order_id": "5346523564",
   "notification_url": "http://merchant.com/notifications",
   "callback_url": "http://merchant.com/callback"
}
```
{% endtab %}

{% tab title="Example Response" %}
```yaml
{
   "id": "D-4-75c7473a-ab86-4e43-bd39-c840268747d3",
   "amount": 100,
   "currency": "ARS",
   "payment_method_id": "MP",
   "payment_method_type": "WALLET",
   "payment_method_flow": "REDIRECT",
   "country": "AR",
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

**Example Asynchronous Notification** 

POST: {payment.notification\_url}

If wallet.save = TRUE, the notification will include a wallet.token as long as the user authenticated successfully \(regardless of if the payment was approved or not\).

```yaml
{
   "id": "D-4-75c7473a-ab86-4e43-bd39-c840268747d3",
   "amount": 100.00,
   "status": "VERIFIED",
   "status_detail": "The wallet was verified.",
   "status_code": "700",
   "currency": "USD",
   "country": "AR",
   "payment_method_id": "MP",
   "payment_method_type": "WALLET",
   "payment_method_flow": "REDIRECT",
   "payer": {
       "name": "Thiago Gabriel",
       "email": "thiago@example.com",
       "document": "53033315550"
   },
   "wallet": {
       "token": "W-yu23y4ibnyiu23y4",
       "userid": "45696493593"
   },
   "order_id": "5346523564",
   "notification_url": "http://www.merchant.com/notifications",
   "created_date": "2018-12-26T20:37:20.000+0000"
}
```



### Direct Wallet Payments

Once a wallet.token was obtained, further payments can be processed without the need of redirecting the user to authenticate, and the payment will be done synchronously.

#### Example Request

{% tabs %}
{% tab title="Example Request" %}
**Example Request**

```yaml
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

#### Example body Request

```yaml
{
   "amount": 100,
   "currency": "ARS",
   "country": "AR",
   "payment_method_id": "MP",
   "payment_method_flow": "DIRECT",
   "payer": {
       "name": "Thiago Gabriel",
       "email": "thiago@example.com",
       "document": "53033315550"
   },
   "wallet": {
       "token": "W-yu23y4ibnyiu23y4"
   },
   "order_id": "5346523565",
   "notification_url": "http://merchant.com/notifications",
   "callback_url": "http://merchant.com/callback"
}
```
{% endtab %}

{% tab title="Example Response" %}
```yaml
{
   "id": "D-4-75c7473a-ab86-4e43-bd39-c840268747d3",
   "amount": 100,
   "currency": "ARS",
   "payment_method_id": "MP",
   "payment_method_type": "WALLET",
   "payment_method_flow": "DIRECT",
   "country": "AR",
   "created_date": "2018-12-26T20:37:20.000+0000",
   "status": "PAID",
   "status_detail": "The payment was paid.",
   "status_code": "200",
   "order_id": "5346523565",
   "notification_url": "http://merchant.com/notifications",
   "redirect_url": "https://sandbox.dlocal.com/collect/pay/pay/M-0aa0cc00-094e-11e9-9f92-dbdad3ad0963?xtid=CATH-ST-1545856640-602791137"
}
```
{% endtab %}
{% endtabs %}

### The Wallet Object

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `name` | String | Name of wallet |
| `save` | Boolean | Whether or not a token will be included in the response in order to make future payments. Optional, default = `FALSE`. |
| `token` | String | Token used to make recurring payments to a previously saved wallet. Required for Direct Wallet Payments. |
| `expiration` | String | Expiration \(in days\) of a saved wallet. Optional. |
| `username` | String | User's username in the merchant's website. Required for OneClick. |
| `email` | String | User’s email. Required for OneClick. |
| `recurring_info` | Object | Info of recurring information for the user. Optional \(for MercadoPago\) |
| `verify` | Boolean | If using the request just to verify the wallet, and not creating a payment. Mandatory as `TRUE` if `amount`=0. Default `FALSE`. |
| `capture` | Boolean | Whether or not to immediately capture the charge. When `FALSE`, the charge issues an authorization and will need to be captured later. Default `TRUE`. Optional. |
| `deviceId` | Object | Device information. Check relevant section. Required for MercadoPago. |

#### \*\*\*\*

**The deviceId Object \(for MercadoPago only\)**

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `deviceId` | String | Device web unique identificator. Use dedicated script to collect it. Example: “5cf65fc6c5db631a47471bb0”. Required only if browser is web. |
| `fingerprint` | Object | Used for mobile devices. See example and SDKs following. Required only if used on native mobile app. |

#### **Web**

Add the following script on website:

```javascript
<script src="https://www.mercadopago.com/v2/security.js" view="checkout"></script>
```

#### Mobile

Use the following SDK to get mobile device fingerprint:

Android: https://github.com/mercadopago/px-android

```javascript
new Device(context);
```

iOS: https://github.com/mercadopago/px-ios

```javascript
Device()
```

**Mobile fingerprint example**

```yaml
    "fingerprint": {
   	 "os": "iOS",
   	 "system_version": "8.3",
   	 "ram": 18446744071562067968,
   	 "disk_space": 498876809216,
   	 "model": "MacBookPro9,2",
   	 "free_disk_space": 328918237184,
   	 "vendor_ids": [
   		 {
   			 "name": "vendor_id",
   			 "value": "C2508642-79CF-44E4-A205-284A4F4DE04C"
   		 },
   		 {
   			 "name": "uuid",
   			 "value": "AB28738B-8DC2-4EC2-B514-3ACF330482B6"
   		 }
   	 ],
   	 "vendor_specific_attributes": {
   		 "feature_flash": false,
   		 "can_make_phone_calls": false,
   		 "can_send_sms": false,
   		 "video_camera_available": true,
   		 "cpu_count": 4,
   		 "simulator": true,
   		 "device_languaje": "en",
   		 "device_idiom": "Phone",
   		 "platform": "x86_64",
   		 "device_name": "iPhone Simulator",
   		 "device_family": 4,
   		 "retina_display_capable": true,
   		 "feature_camera": false,
   		 "device_model": "iPhone Simulator",
   		 "feature_front_camera": false
   	 },
   	 "resolution": "375x667"
    }
```

