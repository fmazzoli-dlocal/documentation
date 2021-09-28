---
description: Learn all about the webhooks event types.
---

# Event Types

DLocal supports event notifications for these types of events.

These transaction notifications are sent in near real time as transaction events occur; they contain detailed information about the events.

## **List of available events**

### **Transaction events**

Webhook notification

```text
{
   "uuid": "ISGW-4-86d652010e3c4a1db61ef6420ebf4197",
   "origin": "TRANSACTION_EVENT",
   "payload": {
      ...
   }
}
```

| **Property** | Description |
| :--- | :--- |
| `uuid` | Webhook unique identifier. |
| `origin` | Webhook event key. |
| `payload` | Webhook event body. |

### **Card transaction events**

The following applies to debit/credit transaction events

Webhook `origin` key = TRANSACTION\_EVENT

Webhook `payload` = [Transaction Object](../managing-funds/transaction-history.md#transaction-object)

**Example Request**

```text
{
   "uuid": "ISGW-4-86d652010e3c4a1db61ef6420ebf4197",
   "origin": "TRANSACTION_EVENT",
   "payload": {
       "transaction_id": "ISGC-4-1JEqoK2eZvKYlo2CGGaCQ8Xn",
       "status": "APPROVED",
       "description": "Deposit",
       "type": "credit",
       "created_date": "2021-03-10T10:02:21.898Z",
       "amount": 5126,
       "currency": "COP",
       "card_id": "",
       "card_acceptor": {
           "mid": "",
           "mcc": "",
           "category": "",
           "name": "",
           "zip_code": "",
           "state": "",
           "street": "",
           "city": "",
           "country": ""
       }
   }
}
```

{% hint style="info" %}
You may specify “ALL” key to enable all events**.**
{% endhint %}

  


