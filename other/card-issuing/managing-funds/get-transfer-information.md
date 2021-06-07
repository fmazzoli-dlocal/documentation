# Get Transfer Information

​

This function enables to retrieve account structure information such as transfer Id, amount, currency and status.

You will need it to check transfer status after receiving asynchronous notification.

https://sandbox.dlocal.com/issuing/transfers/{transfer\_id}

Path Parameters

Transfer id provided when transfer was created.

```text
{    "currency": "COP",    "amount": 106,    "transfer_description": "Transfer fund decription",    "notification_url": "http://merchant.dlocal.com/notification",    "merchant_reference": "t4J0RQgsnO",    "destination_account_id": "ISGA-4-a75663b8b0924dbbb62cfd895d11aa80",    "transfer_type": "DISBURSEMENT",    "date": "2021-03-11T18:12:28Z",    "status": "APPROVED",    "transfer_id": "ISGT-4-d9f327b84b5d40adaf59160ee87133f0"} 
```

## Transfer status <a id="transfer-status"></a>

* PENDING - Initial status.
* APPROVED - Transfer was complete.
* REJECTED - Transfer was rejected

