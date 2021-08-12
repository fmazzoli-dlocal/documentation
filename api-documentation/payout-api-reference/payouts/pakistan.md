# Pakistan

### Mandatory parameters bank transfers 

| **Mandatory parameter** | **Description** | Flow Type |
| :--- | :--- | :--- |
| **login** | 32 chars | ALL |
| **pass** | 32 chars | ALL |
| **external\_id** | Max. 100 chars | ALL |
| **beneficiary\_name** | Max. 100 chars | ALL |
| **beneficiary\_lastname** | Max. 100 chars | ALL |
| **country** | PK | ALL |
| **bank\_code** | See bank codes [here](pakistan.md#bank-codes) | ALL |
| **bank\_account** | Mx. 45 chars | ALL |
| **amount** | Max. 2 decimal numbers | ALL |
| **remitter\_full\_name** | Max. 200 chars | ALL |
| **purpose** | Payouts purpose fix to: ISSCVE | B2C |
| **metadata** | "CommercialType": "&lt;one of this values: OFS, FCISS,PT&gt;" [see commercial Types](pakistan.md#commercial-type) | B2C |

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"NASCIMENTO",
"amount":"1100.00",
"currency":"PKR",
"remitter_full_name": "Test",
"country":"PK",
"bank_code":"13",
"bank_account":"PK6200250002000000",
"comments":"this is the 1st comment",
"notification_url":"https:\/\/thisisawebsite.net",
"type":"json"
}


```

### **Commercial Type**

| Type | Description |
| :--- | :--- |
| FCISS | Freelance of Computer and Information Systems Services \(Equivalent to upto USD 1500/individual/month\): Remittances received by resident individuals from reputed overseas IT firms and online platforms on account of freelance of computer and information systems services. |
| OFS | Other Freelance services \(Equivalent to up to USD 1500/individual/month\) Remittances received by resident individuals from reputed overseas online platforms, firms and individuals on account of freelance services other than computer and information services. |
| PT | Pension Transactions \(Remittances received from known International Government and other organizations by resident pensioners on account of pensions only\) |

### **Bank codes**

| Bank Name | Bank Code |
| :--- | :--- |
| Waseela | **01** |
| NATIONAL BANK OF PAKISTAN | 02 |
|  BANK OF PUNJAB | 03 |
| ALLIED BANK LIMITED | 04 |
| Habib Bank Ltd | 05 |
| MUSLIM COMERCIAL BANK  | 06 |
| Askari Bank Limited | 07 |
|  BANK ALHABIB | 08 |
| BANK ALFALAH LIMITED | 09 |
| Burj Bank | 10 |
| Dubai Islamic Bank Ltd  | 11 |
| FAYSAL BANK LIMITED | 12 |
| HABIB METROPOLITAN BANK | 13 |
| MEEZAN BANK LIMITED | 14 |
| SAMBA BANK | 15 |
| SILK BANK  | 16 |
| SONERI BANK LIMITED | 17 |
| NIB BANK  | 18 |
| CITI BANK  | 20 |
| Sindh Bank | 21 |
| KASB BANK LIMITED | 22 |
| FIRST WOMEN BANK LIMITED | 23 |
| BARCLAYS BANK LIMITED  | 24 |
| Oman International Bank | 25 |
| SUMMIT BANK  | 26 |
| BANK ISLAMI PAKISTAN LIMITED | 27 |
| HSBC Bank Limited | 28 |
| UNITED BANK LIMITED | 29 |
| Al Baraka Bank Pakistan Limited | 30 |
| Standard Chartered Bank | 31 |
| BANK OF KHYBER | 32 |
| BANK OF AZAD  JAMMU KASHMIR | 33 |
| FIRST MICRO FINANCE BANK LIMITED | 34 |
| Model Bank | 35 |
| JAHANGIR SIDDIQUI BANK LTD  | 36 |
| DEUTSCHE BANK  | 37 |
| Tameer microfinance bank | 38 |
| Apna Microfinance Bank | 39 |
| U Microfinance Bank | 40 |
| ICBC  | 41 |
| NRSP | 42 |
| MCB Islamic Bank | 43 |
| THE PUNJAB PROVINCIAL COOPERATIVE BANK LTD  | 44 |
| Bank Of Tokyo Mitsubishi Ufj Ltd | 45 |
| Emaan Islamic Banking Silkbank  | 46 |
| Faisal Islamic Bank Of Bahrain | 47 |
| FINCA Micro Finance BankLimited | 48 |
| SME Bank Ltd | 49 |
| ZARAI TARAQIATI BANK LTD | 50 |

