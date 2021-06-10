# Dominican Republic

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
      <td style="text-align:left">See document validations <a href="dominican-republic.md#document-validations">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>document_type</b>
      </td>
      <td style="text-align:left">RN (Registro Nacional Contribuyente), CE (C&#xE9;dula), PASS (Pasaporte)</td>
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
      <td style="text-align:left">DO</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_code</b>
      </td>
      <td style="text-align:left">See bank codes <a href="dominican-republic.md#bank-codes-and-account-format">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_account</b>
      </td>
      <td style="text-align:left">See bank account validations <a href="dominican-republic.md#bank-codes-and-account-format">here</a>
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
  </tbody>
</table>

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678",
"document_id":"101070803",
"document_type":"RN",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"RUIZ",
"country":"DO",
"bank_code":"1",
"bank_account":"1234567891",
"account_type":"S",
"amount":"119148.00",
"comments":"this is the 1st comment",
"currency":"DOP",
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
      <th style="text-align:left">Verification</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Document</td>
      <td style="text-align:left">RN</td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">Numeric</td>
      <td style="text-align:left">
        <p>First digit should be:
          <br />Tipo de persona o contribuyente:
          <br />1- Personas Jur&#xED;dicas (lucrativas)
          <br />4- Personas Jur&#xED;dicas (no lucrativas)
          <br />5- Personas F&#xED;sicas&quot;
          <br />
        </p>
        <p>Should be valid on the local DGII.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Document</td>
      <td style="text-align:left">CE</td>
      <td style="text-align:left">11</td>
      <td style="text-align:left">Numeric</td>
      <td style="text-align:left">last digit - validation algorithm</td>
    </tr>
    <tr>
      <td style="text-align:left">Document</td>
      <td style="text-align:left">PASS</td>
      <td style="text-align:left">Min 7 Max 12</td>
      <td style="text-align:left">Alphanumeric</td>
      <td style="text-align:left">-</td>
    </tr>
  </tbody>
</table>

### **Bank codes and account format**

| Bank Name | Account length  | Bank code |
| :--- | :--- | :--- |
| Banco Popular | 10 | 1 |
| Banco del Progreso | 10 | 2 |
| Banco BHD | 11 | 3 |
| Banco de Reservas | 10 | 4 |
| Banco León | 9 | 5 |
| Banco Santa Cruz | 14 | 6 |
| Citibank | 10 | 7 |
| Scotiabank | 17 | 8 |
| Asoc. Popular | 16 | 9 |
| Banco López de Haro | 10 | 10 |
| Banco BDI | 10 | 11 |
| Banco Promerica | 14 | 12 |
| Banco Vimenca | 12 | 13 |
| Banco Caribe | 10 | 14 |
| Asoc. Cibao | 12 | 15 |
| Banco de las Americas | 10 | 16 |
| Banesco \(Banco Multiple\) | 11 | 17 |
| Banco de Ahorro y Credito Ademi | 10 | 18 |
| Asoc. La Nacional | 12 | 19 |
| Banco Peravia | 10 | 20 |
| Banco Multiple Lafise | 11 | 21 |
| Banco Providencial | 10 | 22 |
| Banco Empire | 10 | 23 |
| Bellbank | 12 | 24 |
| Banco Atlántico | 8 | 25 |
| Banco Unión | 10 | 26 |
| Banco de Ahorro y Credito Federal | 10 | 27 |
| Banco Multiple Activo | 10 | 28 |

