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

\*\*\*\*

| Bank Name | Other Name | Bank Code |
| :--- | :--- | :--- |
| NHTMCP Saigon Thuong Tin | Sacombank | 1 |
| NHTMCP Cong Thuong Vietnam | Vietinbank | 2 |
| NHTMCP Saigon Cong Thuong | Saigonbank | 3 |
| NHTMCP An Binh | ABBank | 4 |
| NHTMCP Dai Duong | OceanBank | 5 |
| NHTMCP Dong Nam A | SeABank | 6 |
| NHTMCP Dai Chung Vietnam | PVcomBank | 7 |
| NHTMCP Xang Dau Petrolimex | PG Bank | 8 |
| NHTMCP Dau Khi Toan Cau | GP Bank | 9 |
| NHTMCP Dong A \* | Dong A Bank  | 10 |
| NHTMCP Dau Tu va Phat Trien Vietnam | BIDV Bank | 11 |
| NHTMCP Kien Long | KienLongBank | 12 |
| NH Nong Nghiep va Phat Trien Nong Thon Vietnam \* | Agribank  | 13 |
| NHTMCP Ban Viet | Vietcapital Bank | 14 |
| NH Vietnam Thuong Tin | VietBank | 15 |
| NH Lien Doanh Viet Nga | VRBank | 16 |
| NHTMCP Ngoai Thuong Vietnam | VCB | 17 |
| NHTMCP A Chau | ACB | 18 |
| NHTMCP Xuat Nhap Khau Vietnam | Eximbank | 19 |
| NHTMCP Tien Phong | TPBank | 20 |
| NHTMCP Sai Gon Ha Noi | SHB | 21 |
| NHTMCP Phat Trien Thanh Pho HCM | HDBank | 22 |
| NHTMCP Quan Doi | MBBank | 23 |
| NHTMCP Vietnam Thinh Vuong | VPBank | 24 |
| NHTMCP Quoc Te Vietnam | VIB | 25 |
| NHTMCP Ky Thuong Vietnam | Techcombank | 26 |
| NHTMCP Phuong Dong | OCB | 27 |
| NHTMCP Quoc Dan | NCB | 28 |
| NHTNHH MTV Hongleong Vietnam | HLBVN | 29 |
| NHTMCP Buu Dien Lien Viet | LienVietPostBank | 30 |
| NHTMCP Bac A | BacABank | 31 |
| NHTMCP Bao Viet | BVB | 32 |
| NHTNHH MTV Shinhan Vietnam | ShinhanVN | 33 |
| NHTNHH MTV Public Vietnam | Public Bank VN | 34 |
| NHTMCP Saigon | SCB | 35 |
| Australia and New Zealand Banking Group | ANZ Vietnam | 36 |
| HSBC Bank Vietnam | HSBC Bank | 37 |
| Vietnam Maritime Commercial Stock Bank | Maritime Bank | 38 |
| Nam A Commercial Join Stock Bank | NamABank | 39 |
| NH Moneygram | MoneygramBank | 40 |
| NH Chinh Sach XHVN | VBSP | 41 |
| NH Phat Trien VN | VDB | 42 |
| Cooperative Bank of Vietnam | CoopBank | 43 |
| Viet A Bank | VAB | 44 |
| NH Xay Dung VN | CBBank | 45 |
| Ngân hàng TNHH Indovina | IVB | 46 |
| Industrial Bank of Korea– Ha Noi branch | IBK - HN | 48 |
| Woori Bank Vietnam | WooriBank | 49 |
| Citibank Bank Viet Nam | Citibank | 51 |
| Standard Chartered Bank Viet Nam Limited | Standard Chartered Bank | 52 |
| United Overseas Bank Viet Nam | UOB Bank | 53 |

