# Uruguay

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
      <td style="text-align:left">See document validations <a href="uruguay.md#document-validations">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>document_type</b>
      </td>
      <td style="text-align:left">only mandatory when document type it is RUT</td>
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
      <td style="text-align:left">UY</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_code</b>
      </td>
      <td style="text-align:left">See bank codes <a href="uruguay.md#bank-codes">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_branch</b>
      </td>
      <td style="text-align:left">Optional if bank_code is ITAU. See bank branch validations <a href="uruguay.md#bank-codes">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_account</b>
      </td>
      <td style="text-align:left">See bank account validations <a href="uruguay.md#bank-account-validations">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>account_type</b>
      </td>
      <td style="text-align:left">
        <p>Only mandatory if bank_code is BROU</p>
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
"external_id":"1234567812345678b",
"document_id":"12345678",
"country":"UY",
"bank_branch":"11",
"bank_account":"1234567",
"account_type":"C",
"currency":"UYU",
"amount":"114848.39",
"type":"json",
"notification_url":"",
"bank_name":"Banco Ita\u00fa",
"bank_code":"113",
"comments":"this is the 1st comment",
"on_hold":"1",
"beneficiary_name":"HOY",
"beneficiary_lastname":"SA",
"address":"Rbla. Rep. de chile 1119, Montevideo",
"city":"",
"postal_code":"",
"email":"thisisanemail@dlocal.com.uy",
"bdate":"",
"extra_info":"{\"this_is_extra:2334/"}",
"bank_province":"",
"bank_city":"",
"bank_branch_name":"",
"document_type":"RUT",
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
      <td style="text-align:left">CI</td>
      <td style="text-align:left">8</td>
      <td style="text-align:left">Numeric</td>
      <td style="text-align:left">Last digit</td>
      <td style="text-align:left">
        <p>8.741.777-1</p>
        <p>87417771</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Document</td>
      <td style="text-align:left">RUT</td>
      <td style="text-align:left">12</td>
      <td style="text-align:left">Numeric</td>
      <td style="text-align:left">Last digit</td>
      <td style="text-align:left">
        <p>21-100342-001-7</p>
        <p>211003420017</p>
      </td>
    </tr>
  </tbody>
</table>

### Bank account validations

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Account format</th>
      <th style="text-align:left">Length</th>
      <th style="text-align:left">Details</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">BROU</td>
      <td style="text-align:left">XXXYYYYYYZ</td>
      <td style="text-align:left">12</td>
      <td style="text-align:left">
        <p>X-&gt; office num.</p>
        <p>Y-&gt; account num.</p>
        <p>Z-&gt; verification digit</p>
      </td>
      <td style="text-align:left">0000427895</td>
    </tr>
    <tr>
      <td style="text-align:left">BHU</td>
      <td style="text-align:left">XXXYYZZZZZZV</td>
      <td style="text-align:left">10</td>
      <td style="text-align:left">
        <p>X-&gt; Bank branch, starts with 0</p>
        <p>Y-&gt; Product num.</p>
        <p>Z-&gt; Account num. filling with 0 on the left</p>
        <p>V-&gt; Verif. digit</p>
      </td>
      <td style="text-align:left">012345678901</td>
    </tr>
    <tr>
      <td style="text-align:left">Citibank</td>
      <td style="text-align:left">XXXXXXXXXX</td>
      <td style="text-align:left">10</td>
      <td style="text-align:left">Filling with 0 on the left Account num. start with 0, 1 or 5</td>
      <td style="text-align:left">0061436006</td>
    </tr>
    <tr>
      <td style="text-align:left">Bandes</td>
      <td style="text-align:left">XXXYYYYYY</td>
      <td style="text-align:left">9</td>
      <td style="text-align:left">
        <p>X-&gt; Bank branch</p>
        <p>Y-&gt; Account num.</p>
      </td>
      <td style="text-align:left">012123456</td>
    </tr>
    <tr>
      <td style="text-align:left">Itau</td>
      <td style="text-align:left">XXXXXXX</td>
      <td style="text-align:left">7</td>
      <td style="text-align:left">Filling with 0 on the left</td>
      <td style="text-align:left">3190373</td>
    </tr>
    <tr>
      <td style="text-align:left">Scotiabank</td>
      <td style="text-align:left">CCCCCCCCII</td>
      <td style="text-align:left">10</td>
      <td style="text-align:left">
        <p>C-&gt; Client num. filling with 0 on the left</p>
        <p>I-&gt; Account id</p>
      </td>
      <td style="text-align:left">1274204300</td>
    </tr>
    <tr>
      <td style="text-align:left">Scotiabank</td>
      <td style="text-align:left">XXXXXXX</td>
      <td style="text-align:left">7</td>
      <td style="text-align:left">Account num filling with 0 on the left</td>
      <td style="text-align:left">0123456</td>
    </tr>
    <tr>
      <td style="text-align:left">Santander</td>
      <td style="text-align:left">XXXXXXXXXXXX</td>
      <td style="text-align:left">12</td>
      <td style="text-align:left">Account num filling with 0 on the left</td>
      <td style="text-align:left">012345678901</td>
    </tr>
    <tr>
      <td style="text-align:left">Nacion</td>
      <td style="text-align:left">XXXXXXXXXXXX</td>
      <td style="text-align:left">12</td>
      <td style="text-align:left">Account num. filling with 0 on the left</td>
      <td style="text-align:left">001234568901</td>
    </tr>
    <tr>
      <td style="text-align:left">BBVA</td>
      <td style="text-align:left">XXXXXXXXX</td>
      <td style="text-align:left">max 9</td>
      <td style="text-align:left">Account num. without filling with 0 on the left Only numeric digits</td>
      <td
      style="text-align:left">20237345 674501433</td>
    </tr>
    <tr>
      <td style="text-align:left">HSBC</td>
      <td style="text-align:left">XXXXXXXXXX</td>
      <td style="text-align:left">10</td>
      <td style="text-align:left">Filling with 0 to the left</td>
      <td style="text-align:left">0003237999</td>
    </tr>
    <tr>
      <td style="text-align:left">Heritage</td>
      <td style="text-align:left">XXXXXXXYY</td>
      <td style="text-align:left">9</td>
      <td style="text-align:left">
        <p>X-&gt; Account num. filling with 0 on the left</p>
        <p>Y-&gt; Sub Account num.</p>
      </td>
      <td style="text-align:left">0003237999</td>
    </tr>
  </tbody>
</table>

### **Bank codes**

Check below the different values that bank\_code parameter can take depending on each country's bank requirements

| **Bank name** | **Bank code** |
| :--- | :--- |
| BROU - Banco de la República Oriental del Uruguay | 001 |
| Banco Hipotecario del Uruguay | 091 |
| Banco Bandes | 110 |
| Banco ITAU | 113 |
| Scotiabank | 128 |
| Banco Santander | 137 |
| Banco Bilbao Vizcaya Argentaria | 153 |
| HSBC Bank | 157 |
| Banque Heritage | 162 |
| Citibank N.A. Sucursal | 205 |
| Banco de la Nación Argentina | 246 |

