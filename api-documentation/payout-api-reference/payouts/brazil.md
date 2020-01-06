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
      <td style="text-align:left">See document&apos;s validations <a href="brazil.md#document-validations">here</a>
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
      <td style="text-align:left">See bank&apos;s codes <a href="brazil.md#codes-for-bank_code-parameter">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_branch</b>
      </td>
      <td style="text-align:left">See bank&apos;s branch validations <a href="brazil.md#bank-accounts-validations">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_account</b>
      </td>
      <td style="text-align:left">See bank account&apos;s validations <a href="brazil.md#bank-accounts-validations">here</a>
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

### Document Validations

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
</table>### Bank accounts' validations

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

### **Codes for bank\_code parameter**

Check below the different values that bank\_code parameter can take depending on each country's bank requirements

| Bank name | Bank code |
| :--- | :--- |
| BANCO ABC BRASIL S.A. | 246 |
| BANCO DA AMAZONIA S.A. | 003 |
| BANCO DO NORDESTE DO BRASIL S.A. | 004 |
| BANCO BONSUCESSO S.A. | 218 |
| BANCO BRADESCO S.A. | 237 |
| BANCO DO BRASIL S.A. | 001 |
| BANCO DE BRASILIA S.A. - BRB | 070 |
| CAIXA ECONOMICA FEDERAL - CEF | 104 |
| CITIBANK N.A. | 477 |
| BANCO COOPERATIVO DO BRASIL S/A - BANCOOB | 756 |
| BANCO DAYCOVAL S.A. | 707 |
| BANESTES S.A. BANCO DO ESTADO DO ESPIRITO SANTO | 021 |
| BANCO DO ESTADO DO PARA S.A. - BANPARA | 037 |
| BANCO DO ESTADO DO RIO GRANDE DO SUL S.A. - BANRISUL | 041 |
| BANCO DO ESTADO DE SERGIPE S.A. - BANESE | 047 |
| HSBC BANK BRASIL S.A. - BANCO MULTIPLO | 399 |
| ITAU UNIBANCO S.A. | 341 |
| BANCO MERCANTIL DO BRASIL S.A. | 389 |
| BANCO MODAL S.A. | 746 |
| BANCO SAFRA S.A. | 422 |
| BANCO SANTANDER BRASIL S.A. | 033 |
| BANCO COOPERATIVO SICREDI S.A. | 748 |
| BANCO INTER | 077 |
| UNICRED NORTE DO PARANA | 084 |
| COOPERATIVA CENTRAL DE CREDITO URBANO/CECRED | 085 |
| BANCO AGIPLAN S.A. | 121 |
| CONFEDERACAO NACIONAL DAS COOPERATIVAS CENTRAIS UNICREDS | 136 |
| BANCO ORIGINAL | 212 |
| NU PAGAMENTOS \(NUBANK\) | 260 |
| PAGSEGURO INTERNET S.A | 290 |
| BANCO BMG S.A. | 318 |
| BANCO C6 S.A. | 336 |
| BANCO PANAMERICANO S.A. | 623 |
| BANCO SOFISA | 637 |
| BANCO VOTORANTIM S.A. | 655 |
| BANCO NEON | 735 |
| BANCO CITIBANK | 745 |

