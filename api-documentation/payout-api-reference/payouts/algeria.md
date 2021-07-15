# Algeria

### Mandatory parameters Mobile Money

| Mandatory parameter | Description |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars |
| **country** | DZ |
| **amount** | Max. 2 decimal numbers |
| **currency** | DZD |
| **phone** | Max. 10 digits - Has to start with 07, 06,05 |

### Example request

```text
{
    "external_id": "68907654",
    "phone": "0734256787",
    "beneficiary_name": "DLOCAL Algeria",
    "country": "DZ",
    "amount": "1000",
    "currency": "DZD",
    "notification_url": "http://google.com",
    "type": "json"
}
```

### 

