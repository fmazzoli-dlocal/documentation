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

### **Bank codes**

| **Bank code** | **Bank name** |
| :--- | :--- |
| 1 | BANCO AMAMBAY S.A. |
| 2 | BANCO ATLAS S.A. |
| 3 | BANCO BASA S.A |
| 4 | BANCO BILBAO VIZCAYA ARGENTARIA PARAGUAY S.A. |
| 5 | BANCO BUSAIF S.A. DE INVERSION Y FOMENTO |
| 6 | BANCO CENTRAL DEL PARAGUAY |
| 7 | BANCO COMERCIAL PARAGUAYO SA |
| 8 | BANCO CONTINENTAL SAECA |
| 9 | BANCO CORPORACION S.A. |
| 10 | BANCO DE DESARROLLO DEL PARAGUAY S.A. |
| 11 | BANCO DE INVERSIONES DEL PARAGUAY |
| 12 | BANCO DE LA NACION ARGENTINA |
| 13 | BANCO DO BRASIL S.A. |
| 14 | BANCO FAMILIAR S.A.E.C.A. |
| 15 | BANCO FINAMERICA SAECA. |
| 16 | BANCO GENERAL S.A. |
| 17 | BANCO GNB PARAGUAY S.A. |
| 18 | BANCO ITAPUA SAECA |
| 19 | BANCO ITAU PARAGUAY S.A. |
| 20 | BANCO NACIONAL DE FOMENTO |
| 21 | BANCO NACIONAL DE TRABAJADORES |
| 22 | BANCO PARA LA COMERCIALIZACION Y LA PRODUCCION S.A \(BANCOP S.A.\) |
| 23 | BANCO PARAGUAYO ORIENTAL DE INVERSION Y FOMENTO S.A. |
| 24 | BANCO REGIONAL S.A.E.C.A. |
| 25 | Banco RIO S.A.E.C.A. |
| 26 | BOLPAR SOCIEDAD ANONIMA |
| 27 | BOLSA DE VALORES Y PRODUCTOS DE ASUNCION S.A. |
| 28 | BRITISH AMERICAN TOBACCO PRODUCTORA DE CIGARILLOS S.A. |
| 29 | CITIBANK N.A. |
| 30 | CRISOL Y ENCARNACIN FINANCIERA S.A. |
| 31 | FINANCIERA EL COMERCIO S.A.E.C.A. |
| 32 | FINANCIERA EXPORTADORA PARAGUAYA S.A. |
| 33 | FINANCIERA PARAGUAYO JAPONESA SAECA |
| 34 | FONPLATA - FONDO FINANCIERO PARA EL DESAROLLO DE LA CUENCA DEL PLATA |
| 35 | GRUPO INTERNACIONAL DE FINANZAS S.A .C.A. \(INTERFISA FINANCIERA\) |
| 36 | HSBC BANK PARAGUAY SA |
| 37 | SUDAMERIS BANK S.A.E.C.A. |
| 38 | SUMMA ASESORIES |
| 39 | VISION BANCO S.A.E.C.A. |
| 40 | FINLANTINA S.A DE FINANZAS |

