# Egypt

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
      <td style="text-align:left"><b>bank_name</b>
      </td>
      <td style="text-align:left">Max. 40 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_branch</b>
      </td>
      <td style="text-align:left">BIC code</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_account</b>
      </td>
      <td style="text-align:left">Max. 45 chars</td>
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

