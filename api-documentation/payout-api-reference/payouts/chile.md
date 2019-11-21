# Chile

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
      <td style="text-align:left">See document&apos;s validations <a href="chile.md#documents-validations">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>beneficiary_name</b>
      </td>
      <td style="text-align:left">Max. 100 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>country</b>
      </td>
      <td style="text-align:left">CL</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_code</b>
      </td>
      <td style="text-align:left">See bank&apos;s codes <a href="chile.md#codes-for-bank_code-parameter">here</a>
      </td>
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
        <p><b>S</b>: for Savings accounts</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>amount</b>
      </td>
      <td style="text-align:left">Max. 2 decimal numbers</td>
    </tr>
  </tbody>
</table>### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678",
"document_id":"123.456.789-10",
"document_type":"RUT",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"RUIZ",
"country":"CL",
"bank_code":"016",
"bank_account":"123456789123",
"account_type":"V",
"amount":"119148.00",
"comments":"this is the 1st comment",
"currency":"CLP",
"extra_info":"{\"this_is_extra:2334/"}",
"notification_url":"https:\/\/thisisawebsite.net\/payments",
"type":"json"
}
```

### Document's validations

<table>
  <thead>
    <tr>
      <th style="text-align:left"><em>Validation</em>
      </th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Length</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Verification digit</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Document</td>
      <td style="text-align:left">RUT</td>
      <td style="text-align:left">8/9</td>
      <td style="text-align:left">Alphanumeric</td>
      <td style="text-align:left">last digit</td>
      <td style="text-align:left">
        <p>33444111-3</p>
        <p>334441113</p>
      </td>
    </tr>
  </tbody>
</table>### **Codes for bank\_code parameter**

Check below the different values that bank\_code parameter can take depending on each country's bank requirements

| Bank name | Bank code |
| :--- | :--- |
| Banco de Chile | 001 |
| Banco Internacional | 009 |
| Banco del Estado de Chile | 012 |
| Scotiabank Chile | 014 |
| Banco Crédito e Inversiones | 016 |
| Banco Bice | 028 |
| HSBC Bank | 031 |
| Banco Santander- Santiago | 037 |
| Itau Corpbanca | 039 |
| ABN Amro Bank Chile | 046 |
| Banco Security | 049 |
| Banco Falabella | 051 |
| Deutsche Bank | 052 |
| Banco Ripley | 053 |
| Rabobank Chile | 054 |
| Banco Consorcio | 055 |
| Banco Penta | 056 |
| BBVA Chile | 504 |
| Banco del Desarrollo | 507 |

