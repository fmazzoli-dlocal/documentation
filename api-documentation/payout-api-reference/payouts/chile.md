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
      <td style="text-align:left">See document validations <a href="chile.md#document-validations">here</a>
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
      <td style="text-align:left">See bank codes <a href="chile.md#bank-codes">here</a>
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
        <p><b>S: </b>for Savings accounts</p>
        <p><b>V:</b> for Vista account<b> </b>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>amount</b>
      </td>
      <td style="text-align:left">Max. 2 decimal numbers</td>
    </tr>
  </tbody>
</table>

### Example request

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

### Document validations

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
</table>

### **Bank codes**

These are the values the **bank\_code parameter** can take in Chile

| Bank Name | Bank Code |
| :--- | :--- |
| Banco Bice | 28 |
| Banco Consorcio | 55 |
| Banco Crédito e Inversiones | 16 |
| Banco de Chile | 1 |
| Banco del Desarrollo | 507 |
| Banco del Estado de Chile | 12 |
| Banco Falabella | 51 |
| Banco Internacional | 9 |
| Banco Ripley | 53 |
| Banco Santander - Santiago | 37 |
| Banco Security | 49 |
| BBVA Chile | 504 |
| Deutsche Bank | 52 |
| HSBC Bank | 31 |
| Itau Corpbanca | 39 |
| Scotiabank Chile | 14 |
| Coopeuch | 672 |



