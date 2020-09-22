# India

### Mandatory parameters Bank Transfer

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | IN |
| **bank\_code** | See bank codes [here ](india.md#bank-codes)- Only mandatory if bank\_branch is not IFSC |
| **bank\_branch** | See bank branch validations [here](india.md#bank-account-validations) |
| **bank\_account** | Max. 45 chars |
| **amount** | Max. 2 decimal numbers |
| **address** | 200 chars |
| **email** | 100 chars |

{% api-method method="post" host="https://api.dlocal.com/api\_curl/cashout\_api" path="/request\_cashout" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="address" type="string" required=false %}
-Max. 200 chars-
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.dlocal.com/api\_curl/cashout\_api" path="/request\_cashout" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="address" type="string" required=false %}
-Max. 200 chars-
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678b",
"beneficiary_name":"RUDRAH",
"beneficiary_lastname":"HASHIMI",
"country":"IN",
"bank_branch":"SBIN0007440",
"bank_account":"12345678912",
"amount":"2064.00",
"address":"Kailash Colony Market, HS-10",
"comments":"this is the 1st comment",
"currency":"INR",
"email":"thisisanemail@dlocal.com",
"phone":"+91 123456789",
"extra_info":"{\"this_is_extra:2334/"}",
"notification_url":"https:\/\/thisisawebsite.net\/payments",
"type":"json"
}
```

| \*\*\*\* |  |
| :--- | :--- |


### Mandatory parameters to Paytm Wallet transfer

To send payouts to a Paytm wallet the merchant will need a different MID to be created.

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **pass** | 32 chars |
| **external\_id** | Max. 100 chars |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | IN |
| **email** | Email or Phone number are the Paytm account number, If email the user is register with phone, email is not mandatory. |
| **phone** | Email or Phone number are the Paytm account number, \(include the country code\) If the user is register with email, phone is not mandatory. |
| **amount** | Max. 2 decimal numbers |

### Bank branch validation

<table>
  <thead>
    <tr>
      <th style="text-align:left"><em>Name</em>
      </th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Length</th>
      <th style="text-align:left">Format</th>
      <th style="text-align:left">Details</th>
      <th style="text-align:left">Verification digit</th>
      <th style="text-align:left">Validation</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">IFSC</td>
      <td style="text-align:left">Alphanumeric</td>
      <td style="text-align:left">11</td>
      <td style="text-align:left">AAAA0XXXXXX</td>
      <td style="text-align:left">
        <p>A -&gt;</p>
        <p>alphabetic</p>
        <p>0 -&gt;</p>
        <p>Zero</p>
        <p>X -&gt;</p>
        <p>Alphanumeric</p>
      </td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">Validated through the list of valid IFSCs published by the RTGS and the
        NEFT</td>
      <td style="text-align:left">INDB0000018</td>
    </tr>
  </tbody>
</table>

### **Bank codes**

We support all banks regulated by the Reserve Bank of India \(RBI\).

| Bank Name | Bank Code |
| :--- | :--- |
| Abhyudaya Coop Bank | 001 |
| Abu Dhabi Commercial Bank | 003 |
| Airtel Payments Bank Limited | 005 |
| Akola Janata Commercial Cooperative Bank | 006 |
| Allahabad Bank | 007 |
| Almora Urban Co-Operative Bank Ltd. | 015 |
| Andhra Bank | 009 |
| Andhra Pragati Grameen Bank | 012 |
| Apna Sahakari Bank Ltd. | 014 |
| Australia & New Zealand Bank | 010 |
| Axis Bank | 172 |
| B N Paribas Bank | 026 |
| Bandhan Bank Limited | 022 |
| Bank of America | 027 |
| Bank of Bahrein & Kuwait | 019 |
| Bank of Baroda | 017 |
| Bank of Ceylon | 021 |
| Bank of India | 024 |
| Bank of Maharashtra | 099 |
| Bank of Tokyo-Mitsubishi | 028 |
| Barclays Bank | 018 |
| Bassein Catholic Co-Op Bank | 016 |
| Bharatiya Mahila Bank Limited | 025 |
| Canara Bank | 035 |
| Capital Local Area Bank Ltd. | 034 |
| Catholic Syrian Bank | 041 |
| Central Bank of India | 029 |
| Chhatrapati Rajarshishahu Coop Bank | 040 |
| Chinatrust Commercial Bank | 043 |
| Citi Bank | 032 |
| Citizen Credit Coop Bank | 030 |
| City Union Bank | 033 |
| Commonwealth Bk of Australia | 042 |
| Corporation Bank | 036 |
| Credit Agricole Corp N Invsmnt Bk | 039 |
| Credit Suisse Ag? | 038 |
| Dena Bank | 023 |
| Deogiri Nagari Sahakari Bank Ltd. Aurangabad | 046 |
| Deutsche Bank | 047 |
| Development Bank of Singapore | 044 |
| Development Credit Bank | 045 |
| Dhanalaxmi Bank | 050 |
| DICGC | 048 |
| Doha Bank Qsc | 052 |
| Dombivli Nagari Sahakari Bank Ltd. | 051 |
| Equitas Small Finance Bank Limited | 054 |
| Export Import Bank of India | 053 |
| Firstrand Bank | 056 |
| Gurgaon Gramin Bank Ltd. | 059 |
| HDFC Bank Ltd. | 062 |
| Himachal Pradesh State Cooperative Bank Ltd. | 063 |
| Hong Kong & Shanghai Bank | 064 |
| ICICI Bank Ltd. | 070 |
| IDBI Bank | 067 |
| IDFC Bank Limited | 071 |
| Idukki District Co Operative Bank Ltd. | 073 |
| Indian Bank | 072 |
| Indian Overseas Bank | 075 |
| Indus-Ind Bank | 074 |
| Industrial And Commercial Bank of China Limited | 069 |
| Industrial Bank of Korea | 068 |
| Ing Vysya Bank | 177 |
| Jalgaon Janata Sahakari | 079 |
| Janaseva Sahakari Bank Borivli Limited | 078 |
| Janata Sahakari Bank Ltd. \(Pune\) | 082 |
| Jankalyan Shakari Bank | 081 |
| Janseva Shahkari Bank Ltd. Pune | 077 |
| JP Morgan Chase Bank | 031 |
| Kallappanna Awade Ich Janata S | 084 |
| Kapole Bank | 087 |
| Karnataka Bank | 086 |
| Karnataka Gramin Vikas Bank | 097 |
| Karur Vysya Bank | 096 |
| Keb Hana Bank | 094 |
| Kerala Gramin Bank | 091 |
| Kotak Mahindra Bank | 090 |
| Mahanagar Coop Bank | 101 |
| Maharashtra Gramin Bank | 100 |
| Maharashtra State Cooperative Bank | 104 |
| Mashreq Bank | 105 |
| Mizuho Corporate Bank Ltd. | 103 |
| Mumbai District Central Co-Op Bank | 102 |
| Nagar Urban Co Operative Bank | 118 |
| Nagpur Nagrik \(Nnsb Ltd.\*\) | 110 |
| National Australia Bank Limited | 108 |
| National Bank of Abu Dhabi PJSC | 109 |
| New India Co-Operative Bank | 111 |
| NKGSB Bank | 112 |
| North Malbar Gramin Bank | 114 |
| Nutan Nagarik Sahakari Bank | 115 |
| Oman International Bank | 119 |
| Oriental Bank of Commerce | 120 |
| Parsik Janata Sahakari Bank | 121 |
| Paytm Payments Bank Ltd. | 183 |
| Pragathi Krishna Gramin Bank | 122 |
| Prathama Bank | 125 |
| Prime Co Operative Bank Ltd. | 124 |
| PT Bank Maybank Indonesia TBK | 066 |
| Punjab And Maharashtra Co-Op Bank | 123 |
| Punjab And Sind Bank | 126 |
| Punjab National Bank | 128 |
| Rabobank International \(CCRB\) | 129 |
| Rajgurunagar Sahakari Bank Limited | 133 |
| Rajkot Nagarik Sahakari Bank Ltd. | 132 |
| Reserve Bank of India | 131 |
| Sahebrao Deshmukh Cooperative Bank Limited | 136 |
| Samarth Sahakari Bank Ltd. | 141 |
| Sberbank | 135 |
| Shikshak Sahakari Bank Limited | 146 |
| Shinhan Bank | 145 |
| Shivalik Mercantile Co Operative Bank Ltd. | 150 |
| Societe Generale | 151 |
| Solapur Janata Sahakari Bank Limited | 148 |
| South Indian Bank | 147 |
| Standard Chartered Bank | 143 |
| State Bank of Bikaner and Jaipur | 137 |
| State Bank of Hyderabad | 138 |
| State Bank of India | 139 |
| State Bank of Mauritius | 155 |
| State Bank of Mysore | 140 |
| State Bank of Patiala | 154 |
| State Bank of Travancore | 142 |
| Sumitomo Mitsui Banking Corporation | 149 |
| Surat National Cooperative Bank Limited | 156 |
| Syndicate Bank | 160 |
| Tamilnadu Merc. Bank | 165 |
| Thane Bharat Sahakari Bank Ltd. | 161 |
| The A.P. Mahesh Co-Op Urban Bank | 013 |
| The Ahmedabad Merc Coop Bank | 008 |
| The Akola District Central Cooperative Bank | 004 |
| The Andhra Pradesh State Coop Bank | 011 |
| The Bank of Nova Scotia | 116 |
| The Bharat Cooperative Bank | 020 |
| The Cosmos Co-Op. Bank | 037 |
| The Delhi State Cooperative Bank Limited | 049 |
| The Federal Bank | 055 |
| The Gadchiroli District Central Cooperative Bank Limited | 058 |
| The Greater Bombay Co-Op. Bank Ltd. | 057 |
| The Gujarat State Co-Operative Bank | 060 |
| The Hasti Coop Bank Ltd. | 061 |
| The Jalgaon Peopels Cooperative Bank Limited | 080 |
| The Jammu & Kashmir Bank | 076 |
| The Kalupur Comm Coop Bank | 088 |
| The Kalyan Janata Sahakari Bank | 089 |
| The Kangra Central Cooperative Bank | 083 |
| The Kangra Cooperative Bank Ltd. | 085 |
| The Karad Urban Coop Bank Ltd. | 095 |
| The Karnataka State Coop Apex Bank | 093 |
| The Kurmanchal Nagar Sahakari Bank Limited | 092 |
| The Lakshmi Vilas Bank | 098 |
| The Mehsana Urban Cooperative Bank | 106 |
| The Municipal Co Operative Bank Ltd. | 107 |
| The Nainital Bank Ltd. | 117 |
| The Nasik Merchants Co-Op Bank Ltd. | 113 |
| The Pandharpur Urban Co Op. Bank Ltd. Pandharpur | 127 |
| The Rajasthan State Co-Op Bank | 134 |
| The Ratnakar Bank | 130 |
| The Royal Bank of Scotland | 002 |
| The Saraswat Co-Operative Bank | 153 |
| The Seva Vikas Cooperative Bank Limited | 158 |
| The Shamrao Vithal Coop Bank | 159 |
| The Surat District Co-Op Ban | 144 |
| The Surat People's Co-Op Bank | 152 |
| The Sutex Cooperative Bank | 157 |
| The Tamildadu State Apex Coop Bank | 166 |
| The Thane District Central Cooperative Bank Limited | 162 |
| The Thane Janata Sahakari Bank | 164 |
| The Varachha Co-Op. Bank Ltd. | 173 |
| The Vishweshwar Sahakari Bank Ltd. | 175 |
| The West Bengal State Co-Op Bank | 178 |
| The Zoroastrian Cooperative Bank Limited | 181 |
| Tumkur Grain Merchants Co-Op Bank | 163 |
| UBS AG | 168 |
| UCO Bank | 169 |
| Union Bank of India | 167 |
| United Bank of India | 171 |
| United Overseas Bank Limited | 170 |
| Vasai Vikas Sahakari Bank | 176 |
| Vijaya Bank | 174 |
| Westpac Banking Corporation | 179 |
| Woori | 065 |
| Yes Bank | 180 |
| Zila Sahakri Bank Limited Ghaziabad | 182 |

