# Vietnam

### Mandatory parameters

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | VN |
| **bank\_code** | See list here |
| **bank\_account** | Max. 45 chars |
| **amount** | Max. 2 decimal numbers |
| **currency** | USD or VND |
| **phone** | Max. 15 chars |

### Example request

```text
{
    "login":"1n234n56",
    "pass":"HolAc123o",
    "external_id": "#RANDOMALPHANUMERIC:9",
    "document_id": "27836873654",
    "beneficiary_name": "Juan",
    "beneficiary_lastname": "Alonso",
    "country": "VN",
    "bank_code": "13",
    "bank_account": "1234567890",
    "account_type": "C",
    "amount": 10,
    "currency": "VND",
    "type": "json",
    "phone": "09233456",
    "notification_url":"https:\/\/thisisawebsite.net\/payments"
}

```

### **Bank codes**

| Bank Name | Bank Code |
| :--- | :--- |
| NHTMCP Saigon Thuong Tin | 1 |
| NHTMCP Cong Thuong Vietnam | 2 |
| NHTMCP Saigon Cong Thuong | 3 |
| NHTMCP An Binh | 4 |
| NHTMCP Dai Duong | 5 |
| NHTMCP Dong Nam A | 6 |
| NHTMCP Dai Chung Vietnam | 7 |
| NHTMCP Xang Dau Petrolimex | 8 |
| NHTMCP Dau Khi Toan Cau | 9 |
| NHTMCP Dong A \* | 10 |
| NHTMCP Dau Tu va Phat Trien Vietnam | 11 |
| NHTMCP Kien Long | 12 |
| NH Nong Nghiep va Phat Trien Nong Thon Vietnam \* | 13 |
| NHTMCP Ban Viet | 14 |
| NH Vietnam Thuong Tin | 15 |
| NH Lien Doanh Viet Nga | 16 |
| NHTMCP Ngoai Thuong Vietnam | 17 |
| NHTMCP A Chau | 18 |
| NHTMCP Xuat Nhap Khau Vietnam | 19 |
| NHTMCP Tien Phong | 20 |
| NHTMCP Sai Gon Ha Noi | 21 |
| NHTMCP Phat Trien Thanh Pho HCM | 22 |
| NHTMCP Quan Doi | 23 |
| NHTMCP Vietnam Thinh Vuong | 24 |
| NHTMCP Quoc Te Vietnam | 25 |
| NHTMCP Ky Thuong Vietnam | 26 |
| NHTMCP Phuong Dong | 27 |
| NHTMCP Quoc Dan | 28 |
| NHTNHH MTV Hongleong Vietnam | 29 |
| NHTMCP Buu Dien Lien Viet | 30 |
| NHTMCP Bac A | 31 |
| NHTMCP Bao Viet | 32 |
| NHTNHH MTV Shinhan Vietnam | 33 |
| NHTNHH MTV Public Vietnam | 34 |
| NHTMCP Saigon | 35 |
| Australia and New Zealand Banking Group | 36 |
| HSBC Bank Vietnam | 37 |
| Vietnam Maritime Commercial Stock Bank | 38 |
| Nam A Commercial Join Stock Bank | 39 |
| NH Moneygram | 40 |
| NH Chinh Sach XHVN | 41 |
| NH Phat Trien VN | 42 |
| Cooperative Bank of Vietnam | 43 |
| Viet A Bank | 44 |
| NH Xay Dung VN | 45 |
| Ngân hàng TNHH Indovina | 46 |
| Industrial Bank of Korea– Ha Noi branch | 48 |
| Woori Bank Vietnam | 49 |
| Vietnam International Commercial Joint Stock Bank | 50 |
| Citibank Bank Viet Nam | 51 |
| Standard Chartered Bank Viet Nam Limited | 52 |
| United Overseas Bank Viet Nam | 53 |

