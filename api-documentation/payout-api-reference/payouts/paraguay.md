# Paraguay

### Mandatory parameters

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **document\_type** | See document validations [here](paraguay.md#document-validations) |
| **document\_id** | See document validations [here](paraguay.md#document-validations) |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | PY |
| **currency** | PYG or USD or EUR |
| **bank\_code** | BIC code |
| **bank\_account** | See bank account validations [here.](paraguay.md#bank-account-validations) |
| **amount** | Max. 2 decimal numbers |

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678b",
"document_id":"1234567",
"document_type":"CI",
"beneficiary_lastname":"PEREZ",
"country":"PY",
"bank_code":"NACNPYPA0P3",
"bank_account":"1234567891234567",
"amount":"245.40",
"comments":"this is the 1st comment",
"currency":"PYG",
"extra_info":"{\"this_is_extra:2334/"}",
"notification_url":"https:\/\/thisisawebsite.net\/payments",
"type":"json"
}
```

### Document validations

| Validation | Name | Length | Type | Verification digit |
| :--- | :--- | :--- | :--- | :--- |
| Document | CI | 7 | numeric | N/A |
| Document | RUC | 8 | numeric | CI + validation algorithm |

### Bank account validations

| Validation | Name | Length | Type | Verification digit |
| :--- | :--- | :--- | :--- | :--- |
| Bank account | SIPAP | 16 | numeric | N/A |

{% hint style="info" %}
If the account number has less than 16 digits, zeros should be added to the left side so as to complete the mandatory length.
{% endhint %}

