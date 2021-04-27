# Argentina

### Mandatory parameters

| Mandatory parameter | Description |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **document\_id** | See document validations [here](argentina.md#document-validations) |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | AR |
| **bank\_account** | See bank account validations [here](argentina.md#bank-account-validations) |
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

### **Document validations**

| Validation | Name | Length | Type | Verification digit |
| :--- | :--- | :--- | :--- | :--- |
| Document | CUIT/CUIL | 11 | numeric | last digit |

### Bank account validations

| Validation | Name | Length | Type | Verification digit |
| :--- | :--- | :--- | :--- | :--- |
| Account | CBU/CVU | 22 | numeric | Apply verification algorithm |

### Bank codes

These are the values the **bank\_code parameter** can take in Argentina. We currently support all banks from the ACH Interbanking network.

| **Bank name** | **Bank code** |
| :--- | :--- |
| CVU Account | 000 |
| Bacs Banco de Credito Y Securitizacion | 340 |
| Banco B. I. Creditanstalt | 147 |
| Banco Bradesco Argentina | 336 |
| Banco Cetelem Argentina | 331 |
| Banco CMF | 319 |
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
| Banco Hipotecario | 044 |
| Banco Itau  | 259 |
| Banco Julio | 305 |
| Banco Macro | 285 |
| Banco Mariva | 254 |
| Banco Mas Ventas | 341 |
| Banco Meridian | 281 |
| Banco Municipal de Rosario | 065 |
| Banco Patagonia Sudameris | 034 |
| Banco Piano | 301 |
| Banco Provincia de Tierra Del Fuego | 268 |
| Banco Provincia Del Neuquen | 097 |
| Banco Santander | 072 |
| Banco Roela | 247 |
| Banco Saenz | 277 |
| Banco Supervielle S.A. | 027 |
| Bank Of America, National Associa | 262 |
| Industrial and Commercial Bank of China \(ICBC\) Argentina | 015 |
| BBVA | 017 |
| Bnp Paribas | 266 |
| HSBC Bank Argentina | 150 |
| J P Morgan Chase Bank Sucursal Buenos Aires | 165 |
| BANCO VOII S.A. | 312 |
| Nuevo Banco de Entre Rios | 386 |
| Nuevo Banco de La Rioja | 309 |
| Nuevo Banco de Santa Fe | 330 |
| Nuevo Banco Del Chaco | 311 |
| Nuevo Banco Industrial de Azul | 322 |
| RCI Banque Argentina | 339 |
| Wilobank S.A. | 384 |
| Banco Bica S.A. | 426 |
| Banco Coinag S.A. | 431 |
| Banco Sucredito Regional S.A.U. | 435 |
| Bank of Chine Limited Sucursal Buenos Aires | 515 |
| Brubank S.A.U. | 143 |
| Banco de Comercio S.A.  | 432 |
| Banco Dino S.A. | 448 |

