# Lebanon

### Mandatory parameters bank transfers 

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | LB |
| **bank\_branch** | Swift code |
| **bank\_account** | IBAN |
| **bank\_branch\_name** | Max. 100 chars |
| **amount** | Max. 2 decimal numbers**c** |
| **currency** | LBP or USD |

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"NASCIMENTO",
"country":"LB",
"bank_branch":"ALCVLBBE",
"bank_account":"LB62 0999 0000 0001 0019 0122 9114",
"bank_branch_name":"ALBARAKA BEIRUT" 
"comments":"this is the 1st comment",
"notification_url":"https:\/\/thisisawebsite.net",
"amount":"1100.00",
"currency":"LBP",
"type":"json"
}
```

### Mandatory parameters WALLET

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| login | 32 chars |
| pass | 32 chars |
| external\_id | Max. 100 chars |
| beneficiary\_name | Max. 100 chars |
| beneficiary\_lastname | Max. 100 chars |
| country | LB |
| amount | Max. 2 decimal numbers |
| metadata | “{\“Wallet\“:\“Hawele\“}” |
| phone | country code \(+961 \) and 7 to 8 numbers |
| email | Max. 100 chars |

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"NASCIMENTO",
"country":"LB",
"amount":"1100.00",
"currency":"LBP",
"metadata": {
    "wallet":"hawele"
    },
"email":"juan@gmail.com",
"phone":"+96145678976"
}
```

### 

