# Block/Unblock Card

This function is used to modify the status of a card. The possible status are ACTIVE, INACTIVE, CANCELED.

In Colombia, it is only possible to deactivate \(block\) cards via API. Unblocking must be done offline with provider.

## patch​ <a id="undefined"></a>

https://sandbox.dlocal.com/issuing/cards/{card\_id}

Request

Response

Request

Path Parameters

card\_id

required

string

​

Body Parameters

status

required

string

ACTIVE, INACTIVE or CANCELED

Response

200: OK

```text
{    "card_id": "ISGC-4-51997ba1fa5f49d4b4881dfd6aa9b3d5",    "type": "PHYSICAL",    "status": "ACTIVE",    "card_reference": "EPQFVL0jjS4R",    "created_at": "2021-03-11T13:46:11Z"}
```

​

