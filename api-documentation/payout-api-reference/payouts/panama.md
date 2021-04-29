# Panama

### Mandatory parameters

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Mandatory parameter</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>login</b>
      </td>
      <td style="text-align:left">32 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>pass</b>
      </td>
      <td style="text-align:left">32 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>external_id</b>
      </td>
      <td style="text-align:left">Max. 100 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>document_id</b>
      </td>
      <td style="text-align:left">Passport, Cedula, RUC number</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>beneficiary_name</b>
      </td>
      <td style="text-align:left">Max. 100 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>beneficiary_lastname</b>
      </td>
      <td style="text-align:left">Max.100 chars.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_code</b>
      </td>
      <td style="text-align:left">See bank codes here</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_account</b>
      </td>
      <td style="text-align:left">Max. 45 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>account_type</b>
      </td>
      <td style="text-align:left">
        <p><b>C</b>: for Checking accounts</p>
        <p><b>S: </b>for Savings accounts</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>amount</b>
      </td>
      <td style="text-align:left">Max. 2 decimal numbers</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>country</b>
      </td>
      <td style="text-align:left">PA</td>
    </tr>
  </tbody>
</table>

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678",
"document_id":"1267979689",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"RUIZ",
"bank_code":"016",
"bank_account":"123456789123",
"account_type":"C",
"amount":"1148.00",
"comments":"this is the 1st comment",
"currency":"USD",
"type":"json"
}
```

### **Bank codes** <a id="bank-codes-panama"></a>

These are the values the **bank\_code parameter** can take in Panama

| Bank Name | Bank Code |
| :--- | :--- |
| BANCO NACIONAL DE PANAMA | 1 |
| BANISTMO S.A. | 2 |
| CITIBANK | 3 |
| BANCO GENERAL | 7 |
| DAVIVIENDA | 18 |
| MULTIBANK | 37 |
| TOWERBANK | 40 |
| SCOTIABANK | 42 |
| BICSA | 51 |
| COOPERATIVA PROFESIONALES | 71 |
| CAJA DE AHORROS | 77 |
| BANCO DEL PACÍFICO | 91 |
| METROBANK | 106 |
| BANCO ALIADO | 108 |
| CREDICORP BANK | 110 |
| GLOBAL BANK | 115 |
| BANK OF CHINA | 116 |
| CANAL BANK | 125 |
| BAC INTERNATIONAL BANK | 138 |
| BCT BANK INTERNATIONAL | 139 |
| MMG BANK | 147 |
| ST. GEORGES BANK | 149 |
| BANCO AZTECA | 150 |
| BANCO PICHINCHA PANAMA | 151 |
| BANCO DELTA | 156 |
| BANCO LAFISE | 157 |
| BANESCO | 158 |
| CAPITAL BANK | 159 |
| BANISI | 161 |
| MERCANTIL BANK | 163 |
| BBP BANK | 165 |
| PRIVAL BANK | 167 |
| UNI BANK & TRUST, INC. | 170 |
| BANCO FICOHSA | 172 |
| BANCOLOMBIA | 175 |
| BI-BANK | 178 |
| COOPEDUC | 250 |
| COOESAN | 251 |
| CACECHI | 252 |
| COEDUCO | 253 |
| COOPEVE | 254 |
| COOPERATIVA CRISTOBAL | 500 |
| EDIOACC | 501 |
| ECASESO | 502 |
| COOPRAC, R.L. | 503 |

