# Costa Rica

### Mandatory parameters

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **document\_id** | See document validations [here](costa-rica.md#document-validations) |
| **document\_type** | See document validations [here](costa-rica.md#document-validations) |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | CR |
| **bank\_account** | See bank account validations [here](costa-rica.md#bank-account-validations) |
| **amount** | Max. 2 decimal numbers |
| **address** | Max. 200 chars |

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678b",
"document_id":"123456789",
"document_type":"CI",
"country":"CR",
"bank_account":"12345678912345678",
"amount":"2000.00",
"type":"json",
"notification_url":"",
"comments":"",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"RUIZ",
"address":"calle 12# 12A - 12, La fortuna",
"city":"",
"postal_code":"",
"bdate":"",
"extra_info":"",
"bank_city":"",
"bank_branch_name":"",
}
```

### Document validations

| Validation | Name | Length | Type | Verification digit | Example |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Document | CI | 9 | numeric | No | 123456789 |
| Document | CJ | 10 | numeric | No | 1234567890 |
| Document | CR | 11 to 22 | numeric | No | 1234567890155566 |

### Bank account validations

| _Validation_ | Name | Length | Type | Verification digit | Example |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Bank account | IBAN | 17 | numeric | Apply verification algorithm | 12345678912345678 |



