# China

### Mandatory parameters

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **password** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars - Only han characters |
| **country** | CH |
| **bank\_code** | See bank's codes [here](china.md#codes-for-bank_code-parameter) |
| **bank\_name** | See bank's names [here](china.md#codes-for-bank_code-parameter) - Only han characters |
| **bank\_province** | Only han characters |
| **bank\_city** | Only han characters |
| **bank\_branch** | Only numbers |
| **bank\_branch\_name** | Only han characters |
| **bank\_account** | See bank account's validations [here](china.md#codes-for-bank_code-parameter) |
| **amount** | Max. 2 decimal numbers |

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
"extra_info":"{\"this_is_extra:2334/"}",
"notification_url":"https:\/\/thisisawebsite.net\/payments",
"type":"json"
}
```

### **Codes for bank\_code parameter**

| **Bank** | **Code** |
| :--- | :--- |
| People s Bank of China | **1** |
| Industrial and Commercial Bank | 102 |
| Agricultural Bank of China | 103 |
| Bank of China | 104 |
| China Construction Bank | 105 |
| China Development Bank | 201 |
| Export-Import Bank of China | 202 |
| Agricultural Development of China | 203 |
| Bank of Communications | 301 |
| China CITIC Bank | 302 |

