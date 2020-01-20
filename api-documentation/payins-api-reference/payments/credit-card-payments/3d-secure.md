# 3D-Secure

In some regions 3D-Secure authentication might be mandatory. In such a scenario, the [Create a Payment](https://docs.dlocal.com/api-documentation/payins-api-reference/payments#create-a-payment) function will return a payment with `status` =`PENDING` \(`status_code` = `101` \). The Payment Object will include a 3D-Secure object, containing the URL that the user needs to be redirected to so as to complete the authorization.

Once the user completed the authentication successfully, the payment will be processed and the user will be redirected to the `callback_url` .

### Example Response to Create a Payment <a id="example-response-to-create-a-payment"></a>

```yaml
{
    "id": "D-4-03dd274e-672a-4b11-8d41-b0ad76a7c55d",
    "amount": 474.00,
    "currency": "INR",
    "payment_method_id": "CARD",
    "payment_method_type": "CARD",
    "payment_method_flow": "DIRECT",
    "country": "IN",
    "card": {
        "holder_name": "Nino Deicas",
        "expiration_month": 10,
        "expiration_year": 2040,
        "brand": "VI",
        "last4": "1111"
    },
    "three_dsecure" : {
        "redirect_url" : "http://sandbox.dlocal.com/three-ds/M-64356345634587b3495"
    },
    "created_date": "2018-07-12T17:02:47.000+0000",
    "status": "PENDING",
    "status_detail": "The payment is pending 3D Secure authentication.",
    "status_code": "101",
    "order_id": "waC3GWwRYwAP",
    "notification_url": "http://merchant.com/notification",
    "callback_url": "http://merchant.com/return"
}
```

