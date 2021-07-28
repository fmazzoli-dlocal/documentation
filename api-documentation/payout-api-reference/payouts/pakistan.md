# Pakistan

### Mandatory parameters bank transfers 

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **birth\_country** | ISO 3166- 1alpha -2 code |
| **country** | PK |
| **bank\_code** | See bank codes [here](pakistan.md#bank-codes) |
| **bank\_account** | Mx. 45 chars |
| **amount** | Max. 2 decimal numbers |
| **remitter\_full\_name** | Max. 200 chars |
| **remitter\_birth\_date** | Format: "YYYYMMDD" |
| **remitter\_country** | ISO 3166- 1 alpha -2 code |
| **remitter\_address** | Max. 200 chars |
| **remitter\_document\_type** | Options: WP - Work Permit PASS - International Passport ID - Identification ID RP - Residence Permit |
| **purpose** | Payouts purpose.  |

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"NASCIMENTO",
"birth_country": "PK",
"amount":"1100.00",
"currency":"PKR",
"remitter_full_name": "Test",
"remitter_document": "123456-98",
"remitter_birth_date": "19871110",
"remitter_address": "rem street 123",
"remitter_country": "UK",
"remitter_document_type": "WP",
"country":"PK",
"bank_code":"341",
"bank_account":"PK6200250002000000",
 "purpose": "ISMDCS",
"comments":"this is the 1st comment",
"notification_url":"https:\/\/thisisawebsite.net",
"type":"json"
}


```

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

