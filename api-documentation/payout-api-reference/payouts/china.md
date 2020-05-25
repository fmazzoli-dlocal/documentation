# China

### Mandatory parameters

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars - Only han characters |
| **country** | CH |
| **bank\_code** | See bank codes [here](china.md#bank-codes) |
| **bank\_name** | See bank names [here](china.md#bank-codes) - Only han characters |
| **bank\_province** | Only han characters |
| **bank\_city** | Only han characters |
| **bank\_branch** | Only numbers |
| **bank\_branch\_name** | Only han characters |
| **bank\_account** | See bank account validations [here](china.md#codes-for-bank_code-parameter) |
| **amount** | Max. 2 decimal numbers |
| **phone** | Max. 100 chars |
| **document\_id** | Max. 100 chars \(Resident Identity Card\) |

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678",
"beneficiary_name":"\a1b2c\a1b2c\a1b2c",
"beneficiary_lastname":"LING",
"country":"CN",
"bank_branch":"623052",
"bank_account":"1234567891234",
"bank_city":"\a1b2c\a1b2c\a1b2c",
"bank_province":"\a1b2c\a1b2c\a1b2c",
"bank_branch_name":"\a1b2c\a1b2c\a1b2c\a1b2c\a1b2c\a1b2c",
"amount":"9273.34",
"bank_name":"\a1b2c\a1b2c\a1b2c\a1b2c\a1b2c\a1b2c",
"city":"\a1b2c\a1b2c\a1b2c",
"comments":"this is the 1st comment",
"currency":"CNY",
"phone": "6767658758869",
"document_id": "110102YYYYMMDD888X"
"extra_info":"{\"this_is_extra:2334/"}",
"notification_url":"https:\/\/thisisawebsite.net\/payments",
"type":"json"

}
```

### **Bank codes**

The banks supported may change according to the payment's flow**:**

* [P2P & B2C flow](china.md#p-2-p-and-b-2-c-flow)
* [B2B flow](china.md#b-2-b-flow)

### P2P & B2C flow

We support every bank covered by China UnionPay network.

### B2B flow

| **Bank name** | Abbreviation | Bank code |
| :--- | :--- | :--- |
| Bank of China | BOC | 001 |
| Agricultural Bank of China | ABC | 103 |
| Industrial and Commercial Bank of China | ICBC | 102 |
| China Construction Bank | CCB | 105 |
| Bank of Communications. | BOCOM | 301 |
| Postal Savings Bank of China | PSBC | 403 |
| China Merchants Bank | CMB | 308 |
| China CITIC Bank | CITIC | 302 |
| Ping An Bank | PINGAN | 788 |
| Shanghai Pudong Development Bank | SPDB | 310 |
| Industrial Bank Co.,Ltd | CIB | 309 |
| China Minsheng Bank | CMBC | 305 |
| China Everbright Bank | CEB | 303 |
| China Guangfa Bank | GDB | 789 |
| HSBC Bank | HXB | 790 |
| Bank of Ningbo | NBCB | 791 |
| Bank of Beijing | BCCB | 792 |
| Hengfeng Bank Co. | HFB | 793 |
| China Zheshang Bank | CZB | 316 |
| China Bohai Bank | CBHB | 318 |
| Bank of Shanghai | BOS | 794 |
| Bank of Jiangsu | JSCB | 795 |





