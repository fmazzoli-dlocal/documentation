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
| **beneficiary\_name** | Max. 100 chars |
| **country** | PY |
| **currency** | PYG or USD or EUR |
| **bank\_account** | See bank account validations [here.](paraguay.md#bank-account-validations) |
| **bank\_code** | See bank code list here. |
| **amount** | Max. 2 decimal numbers |

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678b",
"document_id":"1234567",
"document_type":"CI",
"beneficiary_name": "Juan"
"beneficiary_lastname":"PEREZ",
"country":"PY",
"bank_account":"1234567891234567",
"bank_code": "11",
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

### **Banks**

| **Bank name** | Bank Code |
| :--- | :--- |
| BANCO AMAMBAY S.A. | 1 |
| BANCO ATLAS S.A. | 2 |
| BANCO BASA S.A | 3 |
| BANCO BILBAO VIZCAYA ARGENTARIA PARAGUAY S.A. | 4 |
| BANCO BUSAIF S.A. DE INVERSION Y FOMENTO | 5 |
| BANCO CENTRAL DEL PARAGUAY | 6 |
| BANCO COMERCIAL PARAGUAYO SA | 7 |
| BANCO CONTINENTAL SAECA | 8 |
| BANCO CORPORACION S.A. | 9 |
| BANCO DE DESARROLLO DEL PARAGUAY S.A. | 10 |
| BANCO DE INVERSIONES DEL PARAGUAY | 11 |
| BANCO DE LA NACION ARGENTINA | 12 |
| BANCO DO BRASIL S.A. | 13 |
| BANCO FAMILIAR S.A.E.C.A. | 14 |
| BANCO FINAMERICA SAECA. | 15 |
| BANCO GENERAL S.A. | 16 |
| BANCO GNB PARAGUAY S.A. | 17 |
| BANCO ITAPUA SAECA | 18 |
| BANCO ITAU PARAGUAY S.A. | 19 |
| BANCO NACIONAL DE FOMENTO | 20 |
| BANCO NACIONAL DE TRABAJADORES | 21 |
| BANCO PARA LA COMERCIALIZACION Y LA PRODUCCION S.A \(BANCOP S.A.\) | 22 |
| BANCO PARAGUAYO ORIENTAL DE INVERSION Y FOMENTO S.A. | 23 |
| BANCO REGIONAL S.A.E.C.A. | 24 |
| Banco RIO S.A.E.C.A. | 25 |
| BOLPAR SOCIEDAD ANONIMA | 26 |
| BOLSA DE VALORES Y PRODUCTOS DE ASUNCION S.A. | 27 |
| BRITISH AMERICAN TOBACCO PRODUCTORA DE CIGARILLOS S.A. | 28 |
| CITIBANK N.A. | 29 |
| CRISOL Y ENCARNACIN FINANCIERA S.A. | 30 |
| FINANCIERA EL COMERCIO S.A.E.C.A. | 31 |
| FINANCIERA EXPORTADORA PARAGUAYA S.A. | 32 |
| FINANCIERA PARAGUAYO JAPONESA SAECA | 33 |
| FONPLATA - FONDO FINANCIERO PARA EL DESAROLLO DE LA CUENCA DEL PLATA | 34 |
| GRUPO INTERNACIONAL DE FINANZAS S.A .C.A. \(INTERFISA FINANCIERA\) | 35 |
| HSBC BANK PARAGUAY SA | 36 |
| SUDAMERIS BANK S.A.E.C.A. | 37 |
| SUMMA ASESORIES | 38 |
| VISION BANCO S.A.E.C.A. | 39 |
| FINLANTINA S.A DE FINANZAS | 40 |

