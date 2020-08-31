# Ghana

| `payment_ method_id` | **Name** | `payment_` `method_type` | `brand` | **Details** | Allowed Flows | **Logos** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `MW` | Mobile Money | `BANK_TRANSFER` |  | Mobile Money | `DIRECT` | ​ |

For Wallet payments in Ghana in particular, the `network` object is required. It has the `metadata.mobile_carrier` parameter. The possible values  for that parameter are `MTN`, `VODAFONE` or `TIGO`.

### Example Request

```yaml
{
    "amount": 100,
    "currency": "GHS",
    "country": "GH",
    "payment_method_id": "MW",
    "payment_method_flow": "DIRECT",
    "payer": {
        "name": "Thiago Gabriel",
        "email": "thiago@example.com",
        "document": "52463567015"
    },
    "network": {
        "metadata.mobile_carrier": "MTN",
    },
    "order_id": "623576234",
    "notification_url": "http://merchant.com/notifications"
}
```

