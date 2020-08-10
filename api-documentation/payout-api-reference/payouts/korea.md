# Korea

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | KR |
| **bank\_code** | Max. 40 chars |
| **bank\_account** | Max. 45 chars |
| **amount** | Max. 2 decimal numbers |
| **remitter\_address** | Max. 200 chars |
| **remitter\_full\_name** | Max.200 chars |
| **remitter\_document** | Max. 45 chars |
| **remitter\_city** | Max. 40 chars |
| **remitter\_postal\_code** | Max. 20 chars |
| **remitter\_bith\_date** | Format 'YYYYMMDD' |

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678b",
"beneficiary_name":"RUDRAH",
"beneficiary_lastname":"HASHIMI",
"country":"KR",
"bank_code":"1",
"bank_account":"1234567891772",
"amount":"2064.00",
"currency":"KPW",
"remitter_address":"Kinmaul 1-dong",
"remitter_full_name":"Jang Kyong Su"
"remitter_document":"78969868758"
"remitter_city":"Pyongyang"
"remitter_postal_code":"DPRK"
"remitter_birth_date":"19860219"
}
```



### **Bank codes**

Check below the different values that bank\_code parameter can take depending on each country's bank requirements

| **Bank name** | **Bank code** |
| :--- | :--- |
| Korea Development Bank001 | 1 |
| 부산은행:Busan Bank | 2 |
| IBK기업:Industrial Bank of Korea | 3 |
| KB국민:Kookmin Bank | 4 |
| 제주은행:Jeju Bank | 5 |
| 수협은행:Suhyup Bank | 6 |
| 경남은행:Kyongnam Bank | 7 |
| NH농협:National Agricultural Cooperative Federation | 8 |
| 우리은행:Woori Bank | 9 |
| SC은행:Standard Chartered First Bank Korea | 10 |
| 신한은행:Shinhan Bank | 11 |
| 대구은행:Daegu Bank | 12 |
| 하나은행:Hana Bank | 13 |
| Kakao Bank | 14 |
| Korea Citi Bank | 15 |
| K-Bank | 16 |
| JeonBuk Bank | 17 |

