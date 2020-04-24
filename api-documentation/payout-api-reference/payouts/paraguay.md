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

### **Banks**

| **Bank name** |
| :--- |
| BANCO AMAMBAY S.A. |
| BANCO ATLAS S.A. |
| BANCO BASA S.A |
| BANCO BILBAO VIZCAYA ARGENTARIA PARAGUAY S.A. |
| BANCO BUSAIF S.A. DE INVERSION Y FOMENTO |
| BANCO CENTRAL DEL PARAGUAY |
| BANCO COMERCIAL PARAGUAYO SA |
| BANCO CONTINENTAL SAECA |
| BANCO CORPORACION S.A. |
| BANCO DE DESARROLLO DEL PARAGUAY S.A. |
| BANCO DE INVERSIONES DEL PARAGUAY |
| BANCO DE LA NACION ARGENTINA |
| BANCO DO BRASIL S.A. |
| BANCO FAMILIAR S.A.E.C.A. |
| BANCO FINAMERICA SAECA. |
| BANCO GENERAL S.A. |
| BANCO GNB PARAGUAY S.A. |
| BANCO ITAPUA SAECA |
| BANCO ITAU PARAGUAY S.A. |
| BANCO NACIONAL DE FOMENTO |
| BANCO NACIONAL DE TRABAJADORES |
| BANCO PARA LA COMERCIALIZACION Y LA PRODUCCION S.A \(BANCOP S.A.\) |
| BANCO PARAGUAYO ORIENTAL DE INVERSION Y FOMENTO S.A. |
| BANCO REGIONAL S.A.E.C.A. |
| Banco RIO S.A.E.C.A. |
| BOLPAR SOCIEDAD ANONIMA |
| BOLSA DE VALORES Y PRODUCTOS DE ASUNCION S.A. |
| BRITISH AMERICAN TOBACCO PRODUCTORA DE CIGARILLOS S.A. |
| CITIBANK N.A. |
| CRISOL Y ENCARNACIN FINANCIERA S.A. |
| FINANCIERA EL COMERCIO S.A.E.C.A. |
| FINANCIERA EXPORTADORA PARAGUAYA S.A. |
| FINANCIERA PARAGUAYO JAPONESA SAECA |
| FONPLATA - FONDO FINANCIERO PARA EL DESAROLLO DE LA CUENCA DEL PLATA |
| GRUPO INTERNACIONAL DE FINANZAS S.A .C.A. \(INTERFISA FINANCIERA\) |
| HSBC BANK PARAGUAY SA |
| SUDAMERIS BANK S.A.E.C.A. |
| SUMMA ASESORIES |
| VISION BANCO S.A.E.C.A. |
| FINLANTINA S.A DE FINANZAS |

