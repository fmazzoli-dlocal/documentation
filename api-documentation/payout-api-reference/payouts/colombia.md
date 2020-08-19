# Colombia

### Mandatory parameters

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Mandatory parameter</b>
      </th>
      <th style="text-align:left"><b>Validations</b>
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
      <td style="text-align:left">See document validations <a href="colombia.md#document-validations">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>document_type</b>
      </td>
      <td style="text-align:left">
        <p><b>NIT</b>
        </p>
        <p><b>CC</b>
        </p>
        <p><b>CE </b>-<b> </b>Carnet Extranjeria</p>
        <p><b>PASS </b>- Passport</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>beneficiary_name</b>
      </td>
      <td style="text-align:left">Max. 100 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>beneficiary_lastname</b>
      </td>
      <td style="text-align:left">Max. 100 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>country</b>
      </td>
      <td style="text-align:left">CO</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_code</b>
      </td>
      <td style="text-align:left">See bank codes <a href="colombia.md#bank-codes">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_account</b>
      </td>
      <td style="text-align:left">See bank account validations <a href="colombia.md#bank-account-validations">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>account_type</b>
      </td>
      <td style="text-align:left">
        <p><b>C</b>: for Checking accounts</p>
        <p><b>S</b>: for Savings accounts</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>amount</b>
      </td>
      <td style="text-align:left">Max. 2 decimal numbers</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>address</b>
      </td>
      <td style="text-align:left">Max. 200 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>email</b>
      </td>
      <td style="text-align:left">Email format - Max. 100 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>phone</b>
      </td>
      <td style="text-align:left">Max. 20 chars</td>
    </tr>
  </tbody>
</table>

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678b",
"document_id":"123.456.789-10",
"country":"CO",
"bank_branch":"",
"bank_account":"1234567891",
"account_type":"C",
"currency":"COP",
"amount":"2000000000.00",
"type":"json",
"notification_url":"",
"bank_name":"BANCOLOMBIA",
"bank_code":"7",
"comments":"",
"on_hold":"",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"RUIZ",
"address":"calle 12# 12A - 12, Bogota",
"city":"",
"postal_code":"",
"email":"thisisanemail@dlocal.com",
"bdate":"",
"extra_info":"",
"bank_province":"",
"bank_city":"",
"bank_branch_name":"",
"document_type":"NIT",
"purpose":"",
}
```

### Document validations

<table>
  <thead>
    <tr>
      <th style="text-align:left">Validation</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Length</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Verification digit</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Document</td>
      <td style="text-align:left">CC</td>
      <td style="text-align:left">Between 6 to 10</td>
      <td style="text-align:left">numeric</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">
        <p>1.004.922.993</p>
        <p>1004922993</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Document</td>
      <td style="text-align:left">NIT</td>
      <td style="text-align:left">10</td>
      <td style="text-align:left">numeric</td>
      <td style="text-align:left">Last digit</td>
      <td style="text-align:left">
        <p>800.198.456-1</p>
        <p>8001984561</p>
      </td>
    </tr>
  </tbody>
</table>

### Bank account validations

Some banks require a specific structure for the bank\_account field:

| Bank | Bank code | Savings length | Checking length | Saving acc. example | Checking acc. Example |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Popular | 002 | 9 | 9 | 620630925 | 645324752 |
| Santander | 006 | 9 | 9 | 272132139 | 963828523 |
| Bancolombia | 007 | 11 | 11 | 27213213912 | 96382852354 |
| HSBC | 010 | 15 | 15 | 208342345908754 | 102938455738947 |
| Sudameris | 012 | 8 | 11 | 208342345908754 | 102938455738947 |
| BBVA | 013 | 16 | 16 | 1234567890123456 | 1234567890123456 |
| Itau | 014 | 9 | 9 | 123456789 | 123456789 |
| Colpatria | 019 | 10 | 10 | 1234567890 | 1234567890 |
| Banco de Occidente | 023 | 9 | 9 | 123456789 | 123456789 |
| Caja social BCSC | 032 | 12 | 12 | 123456789012 | 123456789012 |
| Agrario | 040 | 12 | 12 | 123456789012 | 123456789012 |
| Davivienda | 051 | 12 | 12 | 123456789012 | 123456789012 |
| Av. Villas | 052 | 11 | 13 | 12345678901 | 1234567890123 |
| Procredit | 058 | 13 | 13 | 1234567890123 | 1234567890123 |
| Pichincha | 060 | 9 | 9 | 123456789 | 123456789 |
| Bancoomeva | 061 | 12 | 12 | 123456789012 | 123456789012 |
| Falabella S.A. | 062 | 12 | 12 | 123456789012 | 123456789012 |
| Coopcentral S.A. | 076 | ------ | 9 | ------ | 123456789 |
| Cooperativa financiera de Antioquía | 283 | ------ | 11 | ------ | 12345678901 |
| Cotrafa cooperativa financiera | 289 | ------ | 13 | ------ | 1234567890123 |
| Confiar | 292 | 9 | 9 | 123456789 | 123456789 |
| Financiera Juriscoop | 296 | ------ | 12 | ------ | 123456789012 |

### **Bank codes**

These are the values the bank\_code parameter can take in Colombia:

| Bank name | Bank code |
| :--- | :--- |
| ABN AMRO | 008 |
| Bancamia S.A. | 059 |
| Banco Agrario | 040 |
| Banco Av. Villas | 052 |
| Banco Caja Social BCSC | 032 |
| Banco Colpatria | 019 |
| Banco Compartir S.A. | 067 |
| Banco Davivienda | 051 |
| Banco de Bogota | 001 |
| Banco de Occidente | 023 |
| Banco Falabella S.A. | 062 |
| Banco Finandina S.A. | 063 |
| Banco Multibank S.A. | 064 |
| Banco Mundo Mujer | 047 |
| Banco Pichincha | 060 |
| Banco Popular | 002 |
| Banco Procredit | 058 |
| Banco Santander | 006 |
| Banco Serfinanza S.A. | 069 |
| Banco Sudameris | 012 |
| Banco W S.A. | 053 |
| Bancoldex S.A. | 031 |
| Bancolombia | 007 |
| Bancoomeva | 061 |
| BBVA | 013 |
| Citibank | 009 |
| Coltefinanciera S.A. | 370 |
| Confiar | 292 |
| Coopcentral S.A. | 076 |
| Cooperativa Financiera de Antioquia | 283 |
| Cotrafa Cooperativa Financiera | 289 |
| Daviplata | 551 |
| Financiera Juriscoop | 296 |
| HSBC | 010 |
| Itau | 014 |
| Nequi | 0507 |

