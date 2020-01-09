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
| **bank\_code** | Mandatory only if bank\_account is not CLABE. See bank codes [here](mexico.md#bank-codes) |
| **bank\_account** | See bank account validations [here.](mexico.md#bank-account-validations) |
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

### Bank account validations

| _Validation_ | Type | Length | Type | Verification digit | Example |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Bank account | CLABE | 18 | numeric | Apply verification algorithm | 032180000118359719 |

### **Bank codes**

Check below the different values that bank\_code parameter can take in Mexico

| Bank Name | Bank Code |
| :--- | :--- |
| ABC Capital | 138 |
| Accival | 614 |
| Actinver | 133 |
| Afirme | 062 |
| Akala | 638 |
| American Express | 103 |
| Asea | 652 |
| Autofin | 128 |
| Azteca | 127 |
| B&B | 610 |
| Bajio | 030 |
| Bamsa | 106 |
| Banamex | 002 |
| Banco Famsa | 131 |
| Bancomext | 006 |
| Bancoppel | 137 |
| Banjercito | 019 |
| Banobras | 009 |
| Banorte | 072 |
| Banregio | 058 |
| Bansefi | 166 |
| Bansi | 060 |
| Barclays | 129 |
| Bbase | 145 |
| BBVA Bancomer | 012 |
| BMonex | 112 |
| BMultiva | 132 |
| Bulltick CB | 632 |
| CB Actinver | 621 |
| CB Intercam | 630 |
| CB JPMorgan | 640 |
| CB Deutsche | 626 |
| CI Bolsa | 631 |
| Cibanco | 143 |
| CLS | 901 |
| Compartamos | 130 |
| Consubanco | 140 |
| Credit Suisse | 126 |
| Deutsche Bank | 124 |
| Estructuradores | 606 |
| Evercore | 648 |
| Finamex | 616 |
| Fincomun | 634 |
| GBM | 601 |
| HDI Seguros | 636 |
| Hipotecaria Federal | 168 |
| HSBC | 021 |
| Inbursa | 036 |
| Indeval | 902 |
| ING | 116 |
| Interacciones | 037 |
| Interbanco | 136 |
| Invex | 059 |
| IXE | 032 |
| JP Morgan | 110 |
| Kuspit | 653 |
| Libertad | 670 |
| Mapfre | 619 |
| Masari | 602 |
| Merrill Lynch | 615 |
| Mifel | 042 |
| Monexcb | 600 |
| Nafin | 135 |
| Oactin | 622 |
| Opciones Empresariales del Noroeste | 659 |
| Order | 637 |
| Profuturo | 620 |
| Reforma | 642 |
| Santander | 014 |
| Scotiabank | 044 |
| Segmty | 651 |
| Skandia Vida | 623 |
| Skandia Operadora | 649 |
| Sofiexpress | 655 |
| Sterling | 633 |
| STP | 646 |
| Su Casita | 629 |
| Telecomm | 647 |
| The Royal Bank | 102 |
| Tiber | 607 |
| Tokyo | 108 |
| UBS Bank | 139 |
| Unagra | 656 |
| Unica | 618 |
| Valmex | 617 |
| Value | 605 |
| Ve Por Mas | 113 |
| Vector | 608 |
| Volkswagen | 141 |
| Walmart | 134 |
| Zurich | 627 |
| Zurichvi | 628 |

