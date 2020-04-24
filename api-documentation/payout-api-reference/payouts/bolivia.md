# Bolivia

### Mandatory parameters

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **document\_id** | See document validations [here](brazil.md#document-validations) |
| **document\_type** | See document validations [here](brazil.md#document-validations) |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | BO |
| **bank\_code** | See bank codes [here](brazil.md#bank-codes) |
| **bank\_account** | See account validations here |
| **amount** | Max. 2 decimal numbers |

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678",
"document_id":"123.456.789-10",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"GOMEZ",
"country":"B0",
"bank_code":"1",
"bank_account":"9087654321",
"comments":"this is the 1st comment",
"notification_url":"https:\/\/thisisawebsite.net",
"amount":"1100.00",
"currency":"BOB",
"type":"json"
}
```

### Document validations

| Validation | Name | Length | Type | Verification digit | Example |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Cédula de identidad | CI **** | up to 8 | Numeric | No check digit | 1234567 |
| Cédula de Identidad de extranjero \(Foreign ID number\) | CE |  up to 8 | E - \(numeric\) | No check digit | E-1234567 |
| Número de Identificación Tributaria \(For companies\) | NIT | up to 15 | Numeric |  |  |

### Bank account validations

| Bank name | Validation |
| :--- | :--- |
| Banco Mercantil | Digits length 10 |
| Banco Nacional de Bolivia | Digits length 10 |
| Banco Unión | Digits length 14  |
| Other banks | Digits up to 15 |

### **Bank codes**

| Bank Name | Bank Code |
| :--- | :--- |
| **Banco Mercantil** | 1 |
| **Banco Nacional de Bolivia** | 2 |
| **Banco de Crédito de Bolivia** | 3 |
| **Banco Do Brasil** | 4 |
| **Banco BISA** | 5 |
| **Banco Unión** | 6 |
| **Banco Económico** | 7 |
| **Banco Solidario** | 8 |
| **Banco Ganadero** | 9 |
| **Banco Los Andes Pro Credit** | 10 |
| **Mutual la Primera** | 11 |
| **Mutual Guapay** | 12 |
| **Mutual la Promotora** | 13 |
| **Mutual el Progreso** | 14 |
| **Mutual La Plata** | 15 |
| **Mutual Potosí** | 16 |
| **Mutual la Tarija** | 17 |
| **Mutual Paititi** | 18 |
| **Mutual del Pueblo** | 19 |
| **Mutual Pando** | 20 |
| **Mutual Manutata** | 21 |
| **Cooperativa Jesús Nazareno** | 22 |
| **Cooperativa San Martin** | 23 |
| **Cooperativa Fátima** | 24 |
| **Cooperativa San Pedro** | 25 |
| **Cooperativa Loyola** | 26 |
| **Cooperativa Hospicio** | 27 |
| **Cooperativa San Antonio** | 28 |
| **Cooperativa PIO X** | 29 |
| **Cooperativa Incahuassi** | 30 |
| **Cooperativa Quillacollo** | 31 |
| **Cooperativa San Jose de Punata** | 32 |
| **Cooperativa Trinidad** | 33 |
| **Cooperativa Comarapa** | 34 |
| **Cooperativa San Mateo** | 35 |
| **Cooperativa El Chorolque** | 36 |
| **Cooperativa Educadores Gran Chaco** | 37 |
| **Cooperativa Catedral** | 38 |
| **Magisterio Rural** | 39 |
| **Cooperativa San Joaquín** | 40 |
| **Cooperativa Trapetrol Oriente** | 41 |
| **Nacional Financiera Boliviana SAN** | 42 |
| **Financiera Acceso La Paz** | 43 |
| **Fondo Financiero de la Comunidad** | 44 |
| **Banco FIE** | 45 |
| **Banco Fassil** | 46 |
| **Banco Ecofuturo** | 47 |
| **Banco Prodem** | 48 |
| **Banco Fortaleza** | 49 |

