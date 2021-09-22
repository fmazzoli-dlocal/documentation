# Algeria

### Mandatory parameters Mobile Money

<table>
  <thead>
    <tr>
      <th style="text-align:left">Mandatory parameter</th>
      <th style="text-align:left">Description</th>
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
      <td style="text-align:left"><b>beneficiary_lastname</b>
      </td>
      <td style="text-align:left">Max. 100 chars.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>country</b>
      </td>
      <td style="text-align:left">DZ</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>amount</b>
      </td>
      <td style="text-align:left">Max. 2 decimal numbers</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>currency</b>
      </td>
      <td style="text-align:left">DZD</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>phone</b>
      </td>
      <td style="text-align:left">
        <p>Max. 10 digits - The phone number has to start with 07, 06, 05</p>
        <ul>
          <li>07 - Orascom (Djezzy)</li>
          <li>05 - Ooredoo</li>
          <li>06 - Mobilis</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>metadata</b>
      </td>
      <td style="text-align:left">&#x201C;{\&#x201C;mobile_money\&#x201C;:\&#x201C;YES\&#x201C;}&#x201D;</td>
    </tr>
  </tbody>
</table>

### Example request

```text
{
    "external_id": "68907654",
    "phone": "0734256787",
    "beneficiary_name": "DLOCAL Algeria",
    "country": "DZ",
    "amount": "1000",
    "currency": "DZD",
    "notification_url": "http://google.com",
    "type": "json"
}
```

### 

