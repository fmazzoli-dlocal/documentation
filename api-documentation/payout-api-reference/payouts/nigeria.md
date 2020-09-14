# Nigeria



### Mandatory parameters

| Mandatory parameter | Description |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | NG |
| **bank\_code** | See bank codes here |
| **bank\_account** | See bank account validations here |
| **amount** | Max. 2 decimal numbers |

### Example request

```text
{
"external_id":"1234567812345678",
"beneficiary_name":"Daniela",
"beneficiary_lastname":"Perez",
"country":"NG",
"amount":"4316.50",
"bank_code":"001",
"bank_account":"1234567891234567891234",
"currency":"NGN",
"comments":"this is the 1st comment",
"login":"1n234n56",
"pass":"HolAc123o",
}
```

### Bank account validations

| Validation | Name | Length | Type | Verification digit |
| :--- | :--- | :--- | :--- | :--- |
| Account | NUBAN | 16 | numeric | Apply verification algorithm |

### Bank codes



| **Bank name** | **Bank code** |
| :--- | :--- |
| CENTRAL BANK OF NIGERIA | 001 |
| FIRST BANK OF NIGERIA PLC | 011 |
| NIGERIA INTERNATIONAL BANK \(CITIBANK\) | 023 |
| HERITAGE BANK | 030 |
| UNION BANK OF NIGERIA PLC | 032 |
| UNITED BANK FOR AFRICA PLC | 033 |
| WEMA BANK PLC | 035 |
| ACCESS BANK NIGERIA LTD | 044 |
| ECOBANK NIGERIA PLC | 050 |
| ZENITH INTERNATIONAL BANK LTD | 057 |
| GUARANTY TRUST BANK PLC | 058 |
| FBNQuest Merchant Bank Limited | 060002 |
| DIAMOND BANK LTD | **063** |
| STANDARD CHARTERED BANK NIGERIA LTD | 063 |
| FIDELITY BANK PLC | 070 |
| SKYE BANK PLC | 076 |
| KEYSTONE BANK LTD | 082 |
| IBILE MFB | 090118 |
| HASAL MICROFINANCE BANK | 090121 |
| SUNTRUST BANK | 100 |
| PROVIDUS BANK | 101 |
| FIRST CITY MONUMENT BANK | 214 |
| UNITY BANK PLC | 215 |
| STANBIC IBTC BANK PLC | 221 |
| STERLING BANK PLC | 232 |
| JAIZ BANK PLC | 301 |
| PAGA | 327 |
| RAND MERCHANT BANK | 502 |
| PARALLEX MFB | 526 |
| NPF Microfinance Bank | 552 |
| CORONATION MERCHANT BANK | 559 |
| Page MFBank | 560 |
| New Prudential Bank | 561 |
| FSDH MERCHANT BANK LIMIT | 601 |
| FINATRUST MICROFINANCE BANK | 608 |

