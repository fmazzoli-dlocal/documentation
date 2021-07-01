# Egypt

### Mandatory parameters bank transfer

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
      <td style="text-align:left"><b>beneficiary_name</b>
      </td>
      <td style="text-align:left">Max. 100 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>country</b>
      </td>
      <td style="text-align:left">EG</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_branch</b>
      </td>
      <td style="text-align:left">BIC code (we accept 8 or 11 characters)</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_account</b>
      </td>
      <td style="text-align:left">International Bank Account Number (IBAN)</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>amount</b>
      </td>
      <td style="text-align:left">Max. 2 decimal numbers</td>
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
</table>

### Example request bank transfer

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678b",
"beneficiary_name":"KARIM",
"country":"EG",
"bank_name":"
"bank_branch":"",
"bank_account":"12345678912345678912",
"amount":"245.40",
"address":"Cornish el nil 4455"
"purpose":"ISPAYR",
"currency":"EGP",
"extra_info":"{\"this_is_extra:2334/"}",
"notification_url":"https:\/\/thisisawebsite.net\/payments",
"type":"json"
}
```



### Mandatory parameters Wallets transfer

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
      <td style="text-align:left"><b>beneficiary_name</b>
      </td>
      <td style="text-align:left">Max. 100 chars</td>
    </tr>
    <tr>
      <td style="text-align:left">beneficiary_lastname</td>
      <td style="text-align:left">Max. 100 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>country</b>
      </td>
      <td style="text-align:left">EG</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>phone</b>
      </td>
      <td style="text-align:left">Max. 13 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>metadata</b>
      </td>
      <td style="text-align:left">
        <p>&#x201C;{\&#x201C;wallet\&#x201C;:\&#x201C;&lt;name_of_wallet&gt;\&#x201C;}&#x201D;</p>
        <p> <b>options:</b> vodafone, etisalat, orange, aman, bank_wallet</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>amount</b>
      </td>
      <td style="text-align:left">Max. 2 decimal numbers</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>email</b>
      </td>
      <td style="text-align:left">only mandatory if wallet is aman</td>
    </tr>
  </tbody>
</table>

### Example request wallet

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"7855443",
"beneficiary_name":"KARIM",
"beneficiary_lastname": "Ahan",
"country":"EG",
"phone":"+234567456345
"amount":"245.40",
"email":"karim.ahan@gmail.com"
"currency":"EGP",
"metadata":"{\"wallet\":\“oman\"}" ,
"notification_url":"https:\/\/thisisawebsite.net\/payments",
"type":"json"
}
```



