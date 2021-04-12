# Peru

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
      <td style="text-align:left">See document validations <a href="peru.md#document-validations">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>document_type</b>
      </td>
      <td style="text-align:left">
        <p><b>DNI</b>
        </p>
        <p><b>RUC</b>
        </p>
        <p><b>CE </b>-<b> </b>Carnet Extranjeria</p>
        <p><b>PASS </b>- Passport</p>
        <p>See document validations <a href="peru.md#document-validations">here</a>
        </p>
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
      <td style="text-align:left">PE</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_account</b>
      </td>
      <td style="text-align:left">See bank account validations <a href="peru.md#bank-account-validations">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>account_type</b>
      </td>
      <td style="text-align:left">
        <p><b>C</b>: for Checking accounts</p>
        <p><b>S</b>: for Savings accounts</p>
        <p><b>M</b>: for Maestra accounts</p>
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
"document_type":"DNI",
"beneficiary_name":"JUANA",
"beneficiary_lastname":"PEREZ",
"country":"PE",
"bank_code":"002",
"bank_account":"12345678912345678912",
"account_type":"S",
"amount":"245.40",
"comments":"this is the 1st comment",
"currency":"PEN",
"extra_info":"{\"this_is_extra:2334/"}",
"notification_url":"https:\/\/thisisawebsite.net\/payments",
"type":"json"
}
```

### Document validations

| Validation | Name | Length | Verification digit |
| :--- | :--- | :--- | :--- |
| Document | DNI | 8 Numeric or 9 Alphanumeric | Last digit |
| Document | RUC | 11 Numeric | Last digit |

### Bank account validations

| Validation | Name | Length | Type | Verification digit |
| :--- | :--- | :--- | :--- | :--- |
| Bank account | CCI | 20 | Numeric | Apply verification algorithm |

### **Bank codes**

Check below the different values that bank\_code parameter can take in Peru.

| **Bank** | **Code** |
| :--- | :--- |
| Banco Central de Reserva | 001 |
| Banco de Crédito del Perú | 002 |
| Interbank | 003 |
| Citibank | 007 |
| Scotiabank | 009 |
| BBVA Continental | 011 |
| Banco de la Nación | 018 |
| Banco de Comercio | 023 |
| Banco Financiero | 035 |
| Banco Interamericano de Finanzas \(BIF\) | 038 |
| Crediscotia Financiera | 043 |
| Mi Banco | 049 |
| Banco GNB Perú S.A. | 053 |
| Banco Falabella | 054 |
| Santander | 056 |
| Caja Metropolitana de Lima | 800 |
| Caja Municipal de Ahorro y Crédito Piura SAC | 801 |
| Caja Municipal de Ahorro y Crédito Trujillo | 802 |
| Caja Municipal de Ahorro y Crédito Arequipa | 803 |
| Caja Municipal de Ahorro y Crédito Sullana | 805 |
| Caja Municipal de Ahorro y Crédito Cuzco | 806 |
| Caja Municipal de Ahorro y Crédito Huancayo | 808 |
| Caja Municipal de Ahorro y Crédito Tacna | 813 |

