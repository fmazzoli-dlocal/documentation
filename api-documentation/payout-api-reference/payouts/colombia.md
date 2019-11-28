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
      <td style="text-align:left"><b>password</b>
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
      <td style="text-align:left">See document&apos;s validations <a href="colombia.md#documents-validations">here</a>
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
      <td style="text-align:left">See bank&apos;s codes <a href="colombia.md#codes-for-bank_code-parameter">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_account</b>
      </td>
      <td style="text-align:left">See bank account&apos;s validations <a href="colombia.md#bank-accounts-validations">here</a>
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
</table>### Example request

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

### _Document's validations_

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
      <td style="text-align:left">10</td>
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
</table>### _Bank account's validations_

Some banks require a specific structure for the bank\_account field:

| Bank | Bank code | Savings length | Checking length | Saving acc. example | Checking acc. Example |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Popular | 002 | 9 | 9 | 620630925 | 645324752 |
| Santander | 006 | 9 | 9 | 272132139 | 963828523 |
| Bancolombia | 007 | 11 | 11 | 27213213912 | 96382852354 |
| Citibank | 009 | 10 | 10 | 1005272463 | 1008323387 |
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

### **Codes for bank\_code parameter**

Check below the different values that bank\_code parameter can take depending on each country's bank requirements

| **Bank** | **Code** |
| :--- | :--- |
| BANCO DE BOGOTA | 001 |
| BANCO POPULAR | 002 |
| BANCO SANTANDER | 006 |
| BANCOLOMBIA | 007 |
| ABN AMRO | 008 |
| CITIBANK | 009 |
| HSBC | 010 |
| BANCO SUDAMERIS | 012 |
| BBVA | 013 |
| ITAU | 014 |
| BANCO COLPATRIA | 019 |
| BANCO DE OCCIDENTE | 023 |
| BANCOLDEX S.A. | 031 |
| BANCO CAJA SOCIAL BCSC | 032 |
| BANCO AGRARIO | 040 |
| BANCO MUNDO MUJER | 047 |
| BANCO DAVIVIENDA | 051 |
| BANCO AV VILLAS | 052 |
| BANCO W S.A. | 053 |
| BANCO PROCREDIT | 058 |
| BANCAMIA S.A. | 059 |
| BANCO PICHINCHA | 060 |
| BANCOOMEVA | 061 |
| BANCO FALABELLA S.A | 062 |
| BANCO FINANDINA S.A. | 063 |
| BANCO MULTIBANK S.A. | 064 |
| BANCO COMPARTIR S.A | 067 |
| BANCO SERFINANZA S.A | 069 |
| COOPCENTRAL S.A | 076 |
| COOPERATIVA FINANCIERA DE ANTIOQUIA | 283 |
| COTRAFA COOPERATIVA FINANCIERA | 289 |
| CONFIAR | 292 |
| FINANCIERA JURISCOOP | 296 |
| COLTEFINANCIERA S.A  | 370 |
| NEQUI  | 507 |
| DAVIPLATA | 551 |

