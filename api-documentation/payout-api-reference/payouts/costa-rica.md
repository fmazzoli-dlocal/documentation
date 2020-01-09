# Costa Rica

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
      <td style="text-align:left">See document validations <a href="costa-rica.md#document-validations">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>document_type</b>
      </td>
      <td style="text-align:left">See document validations <a href="costa-rica.md#document-validations">here</a>
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
      <td style="text-align:left">CR</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_account</b>
      </td>
      <td style="text-align:left">See bank account validations <a href="costa-rica.md#bank-account-validations">here</a>
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
      <td style="text-align:left"><b>purpose</b>
      </td>
      <td style="text-align:left">
        <p>6 chars</p>
        <p>See purpose codes <a href="../error-codes-reference.md#purpose-codes-reference">here</a>
        </p>
      </td>
    </tr>
  </tbody>
</table>### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678b",
"document_id":"123456789",
"document_type":"CI"
"country":"CR",
"bank_account":"12345678912345678",
"amount":"2000.00",
"type":"json",
"notification_url":"",
"comments":"",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"RUIZ",
"address":"calle 12# 12A - 12, La fortuna",
"city":"",
"postal_code":"",
"bdate":"",
"extra_info":"",
"bank_city":"",
"bank_branch_name":"",
"purpose":"ISPAYR",
}
```

### Document validations

| Validation | Name | Length | Type | Verification digit | Example |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Document | CI | 9 | numeric | No | 123456789 |
| Document | CJ | 10 | numeric | No | 1234567890 |
| Document | CR | 11 to 22 | numeric | No | 1234567890155566 |

### Bank account validations

| _Validation_ | Name | Length | Type | Verification digit | Example |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Bank account | IBAN | 17 | numeric | Apply verification algorithm | 12345678912345678 |



