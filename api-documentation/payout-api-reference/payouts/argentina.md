# Argentina

### Mandatory parameters

| Mandatory parameter | Description |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **document\_id** | See document's validations [here](argentina.md#documents-validations) |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | AR |
| **bank\_account** | See bank account's validations [here](argentina.md#bank-accounts-validations) |
| **amount** | Max. 2 decimal numbers |

### Example request

```text
{
"external_id":"1234567812345678",
"beneficiary_name":"Daniela",
"beneficiary_lastname":"Perez",
"country":"AR",
"amount":"4316.50",
"bank_name":"BANCO MACRO SA",
"bank_account":"1234567891234567891234",
"document_id":"12345678912",
"currency":"ARS",
"comments":"this is the 1st comment",
"login":"1n234n56",
"pass":"HolAc123o",
}
```

### **Document's validations**

| Validation | Name | Length | Type | Verification digit |
| :--- | :--- | :--- | :--- | :--- |
| Document | CUIT/CUIL | 11 | numeric | last digit |

### Bank account's validations

| Validation | Name | Length | Type | Verification digit |
| :--- | :--- | :--- | :--- | :--- |
| Bank account | CBU | 22 | numeric | Apply verification algorithm |

### **Codes for bank\_code parameter**

Check below the different values that bank\_code parameter can take depending on each country's bank requirements

We support all banks from ACH Interbanking network

| **Bank name** | **Bank code** |
| :--- | :--- |
| A.B.N Amro Bank | 005 |
| American Express Bank Ltd | 295 |
| Bacs Banco de Credito Y Securitizacion | 340 |
| Banca Nazionale Del Lavoro | 265 |
| Banco B. I. Creditanstalt | 147 |
| Banco Bradesco Argentina | 336 |
| Banco Cetelem Argentina | 331 |
| Banco Cofidis | 335 |
| Banco Columbia | 389 |
| Banco Comafi | 299 |
| Banco Credicoop Coop. L | 191 |
| Banco de Corrientes | 094 |
| Banco de Formosa | 315 |
| Banco de Galicia Y Buenos Aires | 007 |
| Banco de Inversion Y Comercio Exterior | 300 |
| Banco de La Ciudad de Buenos Aires | 029 |
| Banco de La Nacion Argentina | 011 |
| Banco de La Pampa Sociedad de Economia M | 093 |
| Banco de La Provincia de Buenos Aires | 014 |
| Banco de La Provincia de Cordoba | 020 |
| Banco de La Republica Oriental Del Uruguay | 269 |
| Banco de San Juan | 045 |
| Banco de Santa Cruz | 086 |
| Banco de Santiago del Estero | 321 |
| Banco de Servicios Financieros | 332 |
| Banco de Servicios Y Transacciones | 338 |
| Banco de Valores | 198 |
| Banco Del Chubut | 083 |
| Banco Del Sol | 310 |
| Banco Del Tucuman | 060 |
| Banco do Brasil | 046 |
| Banco Empresario de Tucuman Coop. L | 137 |
| Banco Finansur | 303 |
| Banco Hipotecario | 044 |
| Banco Itau Buen Ayre | 259 |
| Banco Julio | 305 |
| Banco Macro | 285 |
| Banco Mariva | 254 |
| Banco Mercurio | 293 |
| Banco Meridian | 281 |
| Banco Municipal de Rosario | 065 |
| Banco Patagonia Sudameris | 034 |
| Banco Piano | 301 |
| Banco Privado de Inversiones | 306 |
| Banco Provincia de Tierra Del Fuego | 268 |
| Banco Provincia Del Neuquen | 097 |
| Banco Regional de Cuyo | 079 |
| Banco Santander Rio | 072 |
| Banco Roela | 247 |
| Banco Saenz | 277 |
| Banco Supervielle S.A. | 027 |
| Bank Of America, National Associa | 262 |
| Standard Bank Argentina | 015 |
| BBVA Banco Frances | 017 |
| Bnp Paribas | 266 |
| Citibank | 016 |
| Deutsche Bank | 325 |
| HSBC Bank Argentina | 150 |
| Ing Bank | 294 |
| J P Morgan Chase Bank Sucursal Buenos Aires | 165 |
| Lloyds Tsb Bank | 010 |
| M. B. A. Banco de Inversiones | 312 |
| Nuevo Banco Bisel | 388 |
| Nuevo Banco de Entre Rios | 386 |
| Nuevo Banco de La Rioja | 309 |
| Nuevo Banco de Santa Fe | 330 |
| Nuevo Banco Del Chaco | 311 |
| Nuevo Banco Industrial de Azul | 322 |
| Nuevo Banco Suquia | 387 |
| Rci Ba | 339 |
| The Bank Of Tokyo - Mitsubishi | 018 |
| Banco CMF | 319 |
| Banco Mas ventas | 341 |

