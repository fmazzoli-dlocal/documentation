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

| **Bank name** | Bank Code |
| :--- | :--- |
| People s Bank of China | 1 |
| Industrial and Commercial Bank | 102 |
| Agricultural Bank of China | 103 |
| Bank of China | 104 |
| China Construction Bank | 105 |
| China Development Bank | 201 |
| Export-Import Bank of China | 202 |
| Agricultural Development of China | 203 |
| Bank of Communications | 301 |
| China CITIC Bank | 302 |
| China Everbright Bank | 303 |
| Huaxia Bank | 304 |
| China Minsheng Bank | 305 |
| Guangdong Development Bank | 306 |
| Shenzhen Development Bank | 307 |
| China Merchants Bank | 308 |
| China s Industrial Bank | 309 |
| Shanghai Pudong Development Bank | 310 |
| Dongguan Commercial Bank | 311 |
| Evergrowing Bank | 315 |
| China Zheshang Bank | 316 |
| Bohai Bank | 318 |
| Huishang Bank | 319 |
| Postal Savings Bank of China | 403 |
| Hongkong and Shanghai Banking Corporation | 501 |
| Bank of East Asia | 502 |
| Nanyang Commercial Bank | 503 |
| Hang Seng Bank | 504 |
| Bank of China \(Hongkong\) Ltd | 505 |
| Chiyu Banking Corporation Limited | 506 |
| Chong Hing Bank | 507 |
| DBS Bank \(China\) | 509 |
| Wing Hang Bank | 510 |
| Wing Lung Bank | 512 |
| Citibank | 531 |
| Bank of America | 532 |
| J.P. Morgan Chase | 533 |
| Bank of Tokyo-Mitsubishi UFJ | 561 |
| Sumitomo Mitsui Banking Corporation | 563 |
| Mizuho Corporate Bank | 564 |
| Japan Pass Bank | 565 |
| Korea Exchange Bank | 591 |
| Woori Bank | 593 |
| Korea Development Bank | 594 |
| ShinHan Bank | 595 |
| Industrial Bank of Korea | 596 |
| Hana Bank | 597 |
| Overseas Chinese Banking Corporation | 621 |
| United Overseas Bank | 622 |
| Bangkok Bank | 631 |
| Raiffeisen Zentralbank | 641 |
| KBC Group | 651 |
| Fortis Bank | 652 |
| ABN AMRO Bank | 661 |
| ING Bank | 662 |
| Standard Chartered Bank | 671 |
| The Royal Bank of Scotland | 672 |
| Societe Generate | 691 |
| Banque Indosuez | 694 |
| Natixis | 695 |
| Dresdner Bank AG | 711 |
| Deutsche Bank | 712 |
| Commerzbank | 713 |
| Westdeutsche Landesbank | 714 |
| Bayerische Landesbank AG | 715 |
| Norddeutsche Landesbank | 716 |
| Intesa Sanpaolo | 732 |
| Credit Suisse | 741 |
| Swiss Bank Corp | 742 |
| Bank of Nova Scotia | 751 |
| Bank of Montreal | 752 |
| Australian and New Zealand Bank | 761 |
| Morgan Stanley International Bank | 771 |
| Rabobank | 776 |
| Xiamen International Bank | 781 |
| BNP Paribas | 782 |
| Chinese Mercantile Bank | 785 |
| First Sino Bank | 787 |

