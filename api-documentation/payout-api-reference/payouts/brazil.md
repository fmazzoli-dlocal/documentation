# Brazil

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
      <td style="text-align:left">See document validations <a href="brazil.md#document-validations">here</a>
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
      <td style="text-align:left">BR</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_code</b>
      </td>
      <td style="text-align:left">See bank codes <a href="brazil.md#bank-codes">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_branch</b>
      </td>
      <td style="text-align:left">See bank branch validations <a href="brazil.md#bank-account-validations">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_account</b>
      </td>
      <td style="text-align:left">See bank account validations <a href="brazil.md#bank-account-validations">here</a>
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
</table>### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678",
"document_id":"123.456.789-10",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"NASCIMENTO",
"country":"BR",
"bank_code":"341",
"bank_branch":"0167",
"bank_name":"Itau",
"bank_account":"12345-1",
"account_type":"C",
"comments":"this is the 1st comment",
"notification_url":"https:\/\/thisisawebsite.net",
"amount":"1100.00",
"currency":"BRL",
"type":"json"
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
      <td style="text-align:left">CPF</td>
      <td style="text-align:left">11</td>
      <td style="text-align:left">numeric</td>
      <td style="text-align:left">last two digits</td>
      <td style="text-align:left">
        <p>450.539.758-09</p>
        <p>45053975809</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Document</td>
      <td style="text-align:left">CNPJ</td>
      <td style="text-align:left">14</td>
      <td style="text-align:left">numeric</td>
      <td style="text-align:left">last two digits</td>
      <td style="text-align:left">
        <p>55.694.732/0001-10</p>
        <p>55694732000110</p>
      </td>
    </tr>
  </tbody>
</table>### Bank account validations

Reference

* x --&gt; Numeric character
* D --&gt; Alphanumeric character

| Bank name | Bank branch | Checking account | Savings account |
| :--- | :--- | :--- | :--- |
| Banco do Brasil S.A. | XXXX, XXXXD or XXXX-D | XXXXXXXX or XXXXXXXX-X | XXXXXXXXX or XXXXXXXXX-X Prefixes: 00, 01, 51, 02, 52, 91, 92, 96 or 97 |
| Banco Santander Brasil S.A. | XXXX | XXXXXXXX-X Prefixes: 01, 02, 03, 05, 09, 13 or 92 | XXXXXXXX-X Prefixes: 60 |
| Caixa CEF | XXXX, XXXXX or XXXX-X | XXX.XXXXXXXX-X or any combiantion with or without ',' or '-' characters and prefix or verification code Prefixes: 001, 010, 003 or 023 | XXX.XXXXXXXX-X or any combiantion with or without ',' or '-' characters and prefix or verification code Prefixes: 013 or 022 |
| Banco Bradesco S.A. | XXXX, XXXXX or XXXX-X | XXXXXXX or XXXXXXX-X | XXXXXXX or XXXXXXX-X |
| Itau Unibanco S.A. | XXXX | XXXXX-X | XXXXX-X |
| HSBC Bank Brasil S.A. | XXXX, XXXXD, XXXXDD, XXXX-D or XXXX-DD | XXXXX-XX | XXXXX-XX |
| Other banks | XXXX, XXXXD, XXXXDD, XXXX-D or XXXX-DD | - | - |

### **Bank codes**

These are the values the **bank\_code parameter** can take in Brazil.

| Bank Name | Bank Code |
| :--- | :--- |
| Banco ABC Brasil S.A. | 246 |
| Banco Agiplan S.A. | 121 |
| Banco Bmg S.A. | 318 |
| Banco Bonsucesso S.A. | 218 |
| Banco Bradesco S.A. | 237 |
| Banco C6 S.A. | 336 |
| Banco Citibank | 745 |
| Banco Cooperativo do Brasil S.A. - BANCOOB | 756 |
| Banco Cooperativo Sicredi S.A. | 748 |
| Banco da Amazonia S.A. | 003 |
| Banco Daycoval S.A. | 707 |
| Banco de Brasilia S.A. - BRB | 070 |
| Banco do Brasil S.A. | 001 |
| Banco do Estado de Sergipe S.A. - BANESE | 047 |
| Banco do Estado do Para S.A. - BANPARA | 037 |
| Banco do Estado do Rio Grande do Sul S.A. - BANRISUL | 041 |
| Banco do Nordeste do Brasil S.A. | 004 |
| Banco Inter | 077 |
| Banco Mercantil do Brasil S.A. | 389 |
| Banco Modal S.A. | 746 |
| Banco Neon | 735 |
| Banco Original | 212 |
| Banco Panamericano S.A. | 623 |
| Banco Safra S.A. | 422 |
| Banco Santander Brasil S.A. | 033 |
| Banco Sofisa | 637 |
| Banco Votorantim S.A. | 655 |
| Banestes S.A. Banco do Estado do Espirito Santo | 021 |
| Caixa Economica Federal - CEF | 104 |
| Citibank N.A. | 477 |
| Confederacao Nacional das Cooperativas Centrais Unicreds | 136 |
| Cooperativa Central de Credito Urbano - CECRED | 085 |
| HSBC Bank Brasil S.A. - Banco Multiplo | 399 |
| Itau Unibanco S.A. | 341 |
| Nu Pagamentos \(Nubank\) | 260 |
| Pagseguro Internet S.A | 290 |
| Unicred Norte do Parana | 084 |

