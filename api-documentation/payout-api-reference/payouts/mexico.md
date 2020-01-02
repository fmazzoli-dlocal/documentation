# Mexico

### Mandatory parameters

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | MX |
| **bank\_code** | Mandatory only if bank\_account is not CLABE. See bank's codes [here](mexico.md#codes-for-bank_code-parameter) |
| **bank\_account** | See bank's account validations [here.](mexico.md#banks-account-validations) |
| **amount** | Max. 2 decimal numbers |

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678b",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"PEREZ",
"country":"MX",
"bank_code":"137",
"bank_account":"123456789123456789",
"amount":"2977.89",
"comments":"this is the 1st comment",
"currency":"MXN",
"extra_info":"{\"this_is_extra:2334/"}",
"notification_url":"https:\/\/thisisawebsite.net\/payments",
"type":"json"
}
```

### Bank's account validations

| _Validation_ | Type | Length | Type | Verification digit | Example |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Bank account | CLABE | 18 | numeric | Apply verification algorithm | 032180000118359719 |

### **Codes for bank\_code parameter**

Check below the different values that bank\_code parameter can take depending on each country's bank requirements

| **Bank** | **Code** |
| :--- | :--- |
| BANAMEX | 002 |
| BANCOMEXT | 006 |
| BANOBRAS | 009 |
| BBVA BANCOMER | 012 |
| SANTANDER | 014 |
| BANJERCITO | 019 |
| HSBC | 021 |
| BAJIO | 030 |
| IXE | 032 |
| INBURSA | 036 |
| INTERACCIONES | 037 |
| MIFEL | 042 |
| SCOTIABANK | 044 |
| BANREGIO | 058 |
| INVEX | 059 |
| BANSI | 060 |
| AFIRME | 062 |
| BANORTE | 072 |
| THE ROYAL BANK | 102 |
| AMERICAN EXPRESS | 103 |
| BAMSA | 106 |
| TOKYO | 108 |
| JP MORGAN | 110 |
| BMONEX | 112 |
| VE POR MAS | 113 |
| ING | 116 |
| DEUTSCHE | 124 |
| CREDIT SUISSE | 126 |
| AZTECA | 127 |
| AUTOFIN | 128 |
| BARCLAYS | 129 |
| COMPARTAMOS | 130 |
| BANCO FAMSA | 131 |
| BMULTIVA | 132 |
| ACTINVER | 133 |
| WALMART | 134 |
| NAFIN | 135 |
| INTERBANCO | 136 |
| BANCOPPEL | 137 |
| ABC CAPITAL | 138 |
| UBS BANK | 139 |
| CONSUBANCO | 140 |
| VOLKSWAGEN | 141 |
| CIBANCO | 143 |
| BBASE | 145 |
| BANSEFI | 166 |
| HIPOTECARIA FEDERAL | 168 |
| MONEXCB | 600 |
| GBM | 601 |
| MASARI | 602 |
| VALUE | 605 |
| ESTRUCTURADORES | 606 |
| TIBER | 607 |
| VECTOR | 608 |
| B&B | 610 |
| ACCIVAL | 614 |
| MERRILL LYNCH | 615 |
| FINAMEX | 616 |
| VALMEX | 617 |
| UNICA | 618 |
| MAPFRE | 619 |
| PROFUTURO | 620 |
| CB ACTINVER | 621 |
| OACTIN | 622 |
| SKANDIA | 623 |
| CBDEUTSCHE | 626 |
| ZURICH | 627 |
| ZURICHVI | 628 |
| SU CASITA | 629 |
| CB INTERCAM | 630 |
| CI BOLSA | 631 |
| BULLTICK CB | 632 |
| STERLING | 633 |
| FINCOMUN | 634 |
| HDI SEGUROS | 636 |
| ORDER | 637 |
| AKALA | 638 |
| CB JPMORGAN | 640 |
| REFORMA | 642 |
| STP | 646 |
| TELECOMM | 647 |
| EVERCORE | 648 |
| SKANDIA | 649 |
| SEGMTY | 651 |
| ASEA | 652 |
| KUSPIT | 653 |
| SOFIEXPRESS | 655 |
| UNAGRA | 656 |
| OPCIONES EMPRESARIALES DEL NOROESTE | 659 |
| LIBERTAD | 670 |
| CLS | 901 |
| INDEVAL | 902 |

