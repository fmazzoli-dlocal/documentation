# Brazil

### Mandatory parameters bank transfers

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
</table>

### Example request

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

### Mandatory parameters PIX transfer



| **Mandatory parameter** | **Description** |
| :--- | :--- |
| login | 32 chars |
| pass | 32 chars |
| external\_id | Max. 100 chars |
| document\_id | See document validations [here](brazil.md#document-validations) |
| beneficiary\_name | Max. 100 chars |
| beneficiary\_lastname | Max. 100 chars |
| country | BR |
| amount | Max. 2 decimal numbers |
| metadata | json format: { "pix\_key": &lt;key&gt;} Possible key values: "email"," phone","document\_id","bank\_account"  |
| Key field | It will be mandatory the field that was mention on the metadata field as pix key. |

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678",
"document_id":"123.456.789-10",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"NASCIMENTO",
"country":"BR",
"amount":"1100.00",
"currency":"BRL",
"metadata": {
    "pix_key":"email"
    }
"email":"juan@gmail.com"
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
</table>

### Bank account validations

Reference

* x --&gt; Numeric character
* D --&gt; Alphanumeric character

| Bank name | Bank branch | Checking account | Savings account |
| :--- | :--- | :--- | :--- |
| Banco do Brasil S.A. | XXXX, XXXXD or XXXX-D | XXXXXXXX or XXXXXXXX-X | XXXXXXXXX or XXXXXXXXX-X Prefixes: 00, 01, 51, 02, 52, 91, 92, 96 or 97 |
| Banco Santander Brasil S.A. | XXXX | XXXXXXXX-X Prefixes: 01, 02, 03, 05, 09, 13 or 92 | XXXXXXXX-X Prefixes: 60 |
| Caixa CEF | XXXX, XXXXX or XXXX-X |  XXX.XXXXXXXX-X or any combiantion with or without ',' or '-' characters and prefix or verification code Prefixes: 001, 010, 003 or 023  | XXXX.XXXXXXXXX-X //XXX.XXXXXXXX-X or any combiantion with or without ',' or '-' characters and prefix or verification code Prefixes: 1288 or 013, 022 |
| Banco Bradesco S.A. | XXXX, XXXXX or XXXX-X | XXXXXXX or XXXXXXX-X | XXXXXXX or XXXXXXX-X |
| Itau Unibanco S.A. | XXXX | XXXXX-X | XXXXX-X |
| HSBC Bank Brasil S.A. | XXXX, XXXXD, XXXXDD, XXXX-D or XXXX-DD | XXXXX-XX | XXXXX-XX |
| Other banks | XXXX, XXXXD, XXXXDD, XXXX-D or XXXX-DD | - | - |
| Pix account | no format validation | no  format validation |  |

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
| Kirton Bank S.A. - Banco Multiplo | 399 |
| Itau Unibanco S.A. | 341 |
| Nu Pagamentos \(Nubank\) | 260 |
| Pagseguro Internet S.A | 290 |
| Unicred Norte do Parana | 084 |
| BANCO NACIONAL DE DESENVOLVIMENTO ECONOMICO E SOCIAL | 007 |
| CREDICOAMO CREDITO RURAL COOPERATIVA | 010 |
| CREDIT SUISSE HEDGING-GRIFFO CORRETORA DE VALORES S.A | 011 |
| Banco Inbursa S.A. | 012 |
| STATE STREET BRASIL S.A. – BANCO COMERCIAL | 014 |
| UBS Brasil Corretora de Câmbio Títulos e Valores Mobiliários S.A. | 015 |
| BNY Mellon Banco S.A. | 017 |
| Banco Tricury S.A. | 018 |
| Banco Bandepe S.A. | 024 |
| Banco Alfa S.A. | 025 |
| Banco Itaú Consignado S.A. | 029 |
| Banco Bradesco BBI S.A. | 036 |
| Banco Cargill S.A. | 040 |
| Hipercard Banco Múltiplo S.A. | 062 |
| Banco Bradescard S.A. | 063 |
| GOLDMAN SACHS DO BRASIL BANCO MULTIPLO S.A. | 064 |
| Banco AndBank \(Brasil\) S.A. | 065 |
| BANCO MORGAN STANLEY S.A. | 066 |
| Banco Crefisa S.A. | 069 |
| Banco J. Safra S.A. | 074 |
| Banco ABN Amro S.A. | 075 |
| Banco KDB do Brasil S.A. | 076 |
| Haitong Banco de Investimento do Brasil S.A. | 078 |
| Banco Original do Agronegócio S.A. | 079 |
| BancoSeguro S.A. | 081 |
| BANCO TOPÁZIO S.A. | 082 |
| Banco da China Brasil S.A. | 083 |
| Banco Finaxis S.A. | 094 |
| Travelex Banco de Câmbio S.A. | 095 |
| Banco B3 S.A. | 096 |
| Banco Bocom BBM S.A. | 107 |
| Banco Western Union do Brasil S.A. | 119 |
| BANCO RODOBENS S.A. | 120 |
| Banco Bradesco BERJ S.A. | 122 |
| Banco Woori Bank do Brasil S.A. | 124 |
| Plural S.A. Banco Múltiplo | 125 |
| BR Partners Banco de Investimento S.A. | 126 |
| MS Bank S.A. Banco de Câmbio | 128 |
| UBS Brasil Banco de Investimento S.A. | 129 |
| ICBC do Brasil Banco Múltiplo S.A. | 132 |
| Intesa Sanpaolo Brasil S.A. - Banco Múltiplo | 139 |
| BEXS BANCO DE CÂMBIO S/A | 144 |
| Commerzbank Brasil S.A. - Banco Múltiplo | 163 |
| Banco Olé Bonsucesso Consignado S.A. | 169 |
| Banco Itaú BBA S.A. | 184 |
| Banco BTG Pactual S.A. | 208 |
| Banco Arbi S.A. | 213 |
| Banco John Deere S.A. | 217 |
| BANCO CRÉDIT AGRICOLE BRASIL S.A. | 222 |
| Banco Fibra S.A. | 224 |
| Banco Cifra S.A. | 233 |
| BANCO CLASSICO S.A. | 241 |
| Banco Máxima S.A. | 243 |
| Banco Investcred Unibanco S.A. | 249 |
| BCV - BANCO DE CRÉDITO E VAREJO S.A. | 250 |
| Bexs Corretora de Câmbio S/A | 253 |
| PARANÁ BANCO S.A. | 254 |
| MONEYCORP BANCO DE CÂMBIO S.A. | 259 |
| Banco Fator S.A. | 265 |
| BANCO CEDULA S.A. | 266 |
| HSBC BRASIL S.A. - BANCO DE INVESTIMENTO | 269 |
| Banco de la Nacion Argentina | 300 |
| BPP Instituição de Pagamento S.A. | 301 |
| China Construction Bank \(Brasil\) Banco Múltiplo S/A | 320 |
| BANCO BARI DE INVESTIMENTOS E FINANCIAMENTOS S.A. | 330 |
| Banco Digio S.A. | 335 |
| Banco XP S.A. | 348 |
| BANCO SOCIETE GENERALE BRASIL S.A. | 366 |
| Banco Mizuho do Brasil S.A. | 370 |
| BANCO J.P. MORGAN S.A. | 376 |
| Banco Bradesco Financiamentos S.A. | 394 |
| BANCO CAPITAL S.A. | 412 |
| Banco MUFG Brasil S.A. | 456 |
| Banco Sumitomo Mitsui Brasileiro S.A. | 464 |
| Banco Caixa Geral - Brasil S.A. | 473 |
| Banco ItauBank S.A. | 479 |
| DEUTSCHE BANK S.A. - BANCO ALEMAO | 487 |
| JPMorgan Chase Bank National Association | 488 |
| ING Bank N.V. | 492 |
| Banco Credit Suisse \(Brasil\) S.A. | 505 |
| Banco Luso Brasileiro S.A. | 600 |
| Banco Industrial do Brasil S.A. | 604 |
| Banco VR S.A. | 610 |
| Banco Paulista S.A. | 611 |
| Banco Guanabara S.A. | 612 |
| Omni Banco S.A. | 613 |
| BANCO FICSA S.A. | 626 |
| Banco Smartbank S.A. | 630 |
| Banco Rendimento S.A. | 633 |
| BANCO TRIANGULO S.A. | 634 |
| Banco Pine S.A. | 643 |
| Itaú Unibanco Holding S.A. | 652 |
| BANCO INDUSVAL S.A. | 653 |
| BANCO A.J. RENNER S.A. | 654 |
| Banco Ourinvest S.A. | 712 |
| Banco Cetelem S.A. | 739 |
| BANCO RIBEIRAO PRETO S.A. | 741 |
| Banco Semear S.A. | 743 |
| Banco Rabobank International Brasil S.A. | 747 |
| Scotiabank Brasil S.A. Banco Múltiplo | 751 |
| Banco BNP Paribas Brasil S.A. | 752 |
| Novo Banco Continental S.A. - Banco Múltiplo | 753 |
| Banco Sistema S.A. | 754 |
| Bank of America Merrill Lynch Banco Múltiplo S.A. | 755 |
| BANCO KEB HANA DO BRASIL S.A. | 757 |
| Mercadopago.com Representacoes LTDA | 323 |

