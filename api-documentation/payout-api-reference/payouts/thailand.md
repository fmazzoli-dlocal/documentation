# Thailand

### Mandatory parameters

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | TH |
| **bank\_code** | See list here |
| **bank\_account** | Max. 45 chars |
| **amount** | Max. 2 decimal numbers |
| **currency** | USD or THB |
| **phone** | Max. 15 chars |

### Example request

```text
{
    "login":"1n234n56",
    "pass":"HolAc123o",
    "external_id": "#RANDOMALPHANUMERIC:9",
    "document_id": "275347623546",
    "beneficiary_name": "Lucia",
    "beneficiary_lastname": "Diaz",
    "country": "PH",
    "bank_code": "3",
    "bank_branch": "7890",
    "bank_account": "0213880962",
    "account_type": "S",
    "amount": 10,
    "currency": "THB",
    "type": "json",
    "phone": "8346583658"
    "notification_url":"https:\/\/thisisawebsite.net\/payments"
}

```

### Mandatory parameters wallet

| Mandatory parameter | Description |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | TH |
| **amount** | Max. 2 decimal numbers |
| **currency** | THB |
| **phone** | With or without country code + 10 digits phone |
| **metadata** | “{\“wallet\“:\“truemoney\“}” |

### Example request

```text
{
    "external_id": "68907654",
    "phone": "8756435675",
    "beneficiary_name": "DLOCAL Thailand",
    "beneficiary_lastname": "Limited",
    "country": "TH",
    "amount": "100",
    "currency": "THB",
    "metadata": "{\"wallet\":\"truemoney\"}",
    "notification_url": "http://google.com",
    "type": "json"
}
```

### 

### **Bank codes**

| **Bank Name** | Bank code |
| :--- | :--- |
| BANGKOK BANK | 1 |
| BANK OF AYUDHYA | 2 |
| CIMB Thai Bank Public Company Ltd | 3 |
| GOVERNMENT SAVING BANK | 4 |
| KASIKORN BANK | 5 |
| KRUNG THAI BANK | 6 |
| SIAM COMMERCIAL BANK | 7 |
| THAI MILITARY BANK | 8 |
| THANACHART BANK | 9 |
| UNITED OVERSEA BANK \(Thai\) LTD | 10 |
| CITIBANK | 11 |
| SUMITOMO MITSUI BANKING CORPORATION | 12 |
| STANDARD CHARTERED BANK \(THAI\) | 13 |
| MEGA INTERNATIONAL COMMERCIAL BANK PCL | 14 |
| BANK OF AMERICA NATIONAL ASSOCIATION | 15 |
| HONG KONG & SHANGHAI CORPORATION LIMITED | 16 |
| DEUTSCHE BANK | 17 |
| MIZUHO CORPORATE BANK LIMITED | 18 |
| ISLAMIC BANK OF THAILAND | 19 |
| TISCO BANK PUBLIC COMPANY LIMITED | 20 |
| KIATNAKIN BANK PUBLIC COMPANY LIMITED | 21 |
| THE THAI CREDIT RETAIL BANK PUBLIC COMPANY LIMITED | 22 |
| AGRICULTURE & AGRICULTL COOP | 23 |
| GOVERNMENT HOUSING BANK | 24 |
| LAND AND HOUSES BANK PUBLIC COMPANY LIMITED | 25 |
| INDUSTRIAL AND COMMERCIAL BANK OF CHINA | 26 |

