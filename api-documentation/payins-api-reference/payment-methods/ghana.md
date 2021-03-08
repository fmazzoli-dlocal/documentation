# Ghana

<table>
  <thead>
    <tr>
      <th style="text-align:left"><code>payment_<br />method_id</code>
      </th>
      <th style="text-align:left"><b>Name</b>
      </th>
      <th style="text-align:left"><code>payment_</code>
        <br /><code>method_type</code>
      </th>
      <th style="text-align:left"><code>brand</code>
      </th>
      <th style="text-align:left"><b>Details</b>
      </th>
      <th style="text-align:left">Allowed Flows</th>
      <th style="text-align:left"><b>Logos</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>MW</code>
      </td>
      <td style="text-align:left">Mobile Money</td>
      <td style="text-align:left"><code>BANK_TRANSFER</code>
      </td>
      <td style="text-align:left">Vodafone</td>
      <td style="text-align:left">Mobile Money</td>
      <td style="text-align:left"><code>DIRECT</code>
      </td>
      <td style="text-align:left">&#x200B;<a href="https://static.dlocal.com/images/providers/FW_OR.png">https://static.dlocal.com/images/providers/FW_VF.png</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>MW</code>
      </td>
      <td style="text-align:left">Mobile Money</td>
      <td style="text-align:left"><code>BANK_TRANSFER</code>
      </td>
      <td style="text-align:left">MTN</td>
      <td style="text-align:left">Mobile Money</td>
      <td style="text-align:left"><code>DIRECT</code>
      </td>
      <td style="text-align:left"><a href="https://static.dlocal.com/images/providers/FW_MT.png">&#x200B;</a>
        <a
        href="https://static.dlocal.com/images/providers/FW_MT.png">https://static.dlocal.com/images/providers/FW_MT.png</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>MW</code>
      </td>
      <td style="text-align:left">Mobile Money</td>
      <td style="text-align:left"><code>BANK_TRANSFER</code>
      </td>
      <td style="text-align:left">Tigo</td>
      <td style="text-align:left">Mobile Money</td>
      <td style="text-align:left"><code>DIRECT</code>
      </td>
      <td style="text-align:left">&#x200B;<a href="https://static.dlocal.com/images/providers/FW_OR.png">https://static.dlocal.com/images/providers/FW_TG.png</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>MW</code>
      </td>
      <td style="text-align:left">Mobile Money</td>
      <td style="text-align:left"><code>BANK_TRANSFER</code>
      </td>
      <td style="text-align:left">Airtel</td>
      <td style="text-align:left">Mobile Money</td>
      <td style="text-align:left"><code>DIRECT</code>
      </td>
      <td style="text-align:left"><a href="https://static.dlocal.com/images/providers/FW_MT.png">&#x200B;</a>
        <a
        href="https://static.dlocal.com/images/providers/FW_MT.png">https://static.dlocal.com/images/providers/FW_AT.png</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>CARD</code>
      </td>
      <td style="text-align:left">MasterCard</td>
      <td style="text-align:left"><code>CARD</code>
      </td>
      <td style="text-align:left"><code>MC</code>
      </td>
      <td style="text-align:left">Credit Card</td>
      <td style="text-align:left">
        <p><code>DIRECT</code>
        </p>
        <p><code>REDIRECT</code>
        </p>
      </td>
      <td style="text-align:left">&#x200B;<a href="https://pay.dlocal.com/views/2.0/images/payments/MC.png">https://pay.dlocal.com/views/2.0/images/payments/MC.png</a>&#x200B;</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>CARD</code>
      </td>
      <td style="text-align:left">Visa Debit</td>
      <td style="text-align:left"><code>CARD</code>
      </td>
      <td style="text-align:left"><code>VD</code>
      </td>
      <td style="text-align:left">Debit Card</td>
      <td style="text-align:left">
        <p><code>DIRECT</code>
        </p>
        <p><code>REDIRECT</code>
        </p>
      </td>
      <td style="text-align:left">&#x200B;<a href="https://pay.dlocal.com/views/2.0/images/payments/VD.png">https://pay.dlocal.com/views/2.0/images/payments/VD.png</a>&#x200B;</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>CARD</code>
      </td>
      <td style="text-align:left">Mastercard Debit</td>
      <td style="text-align:left"><code>CARD</code>
      </td>
      <td style="text-align:left"><code>MD</code>
      </td>
      <td style="text-align:left">Debit Card</td>
      <td style="text-align:left">
        <p><code>DIRECT</code>
        </p>
        <p><code>REDIRECT</code>
        </p>
      </td>
      <td style="text-align:left">&#x200B;<a href="https://pay.dlocal.com/views/2.0/images/payments/MD.png">https://pay.dlocal.com/views/2.0/images/payments/MD.png</a>&#x200B;</td>
    </tr>
  </tbody>
</table>

### Mobile Money payments in Ghana

For Mobile Money payments in Ghana in particular, the `network` object is required. It has the `metadata.mobile_carrier` parameter. The possible values  for that parameter are `MTN`, `VODAFONE` or `TIGO`.

### Example Request

```yaml
{
    "amount": 100,
    "currency": "GHS",
    "country": "GH",
    "payment_method_id": "MW",
    "payment_method_flow": "DIRECT",
    "payer": {
        "name": "Thiago Gabriel",
        "email": "thiago@example.com",
        "document": "52463567015"
    },
    "metadata": {
        "mobile_carrier": "MTN",
    },
    "order_id": "623576234",
    "notification_url": "http://merchant.com/notifications"
}
```

