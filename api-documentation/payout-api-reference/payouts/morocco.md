# Morocco



### Mandatory parameters

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | MA |
| **bank\_account** | RIB length 24 digits |
| **amount** | Max. 2 decimal numbers |

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678b",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"PEREZ",
"country":"MA",
"bank_account":"007787001988877665431292",
"amount":"2977.89",
"comments":"this is the 1st comment",
"currency":"MAD",
"extra_info":"{\"this_is_extra:2334/"}",
"notification_url":"https:\/\/thisisawebsite.net\/payments",
"type":"json"
}
```

### Bank account validations

| _Validation_ | Type | Length | Type | Verification  |
| :--- | :--- | :--- | :--- | :--- |
| Bank account | RIB | 24 | numeric | Validate length |

### \*\*\*\*



