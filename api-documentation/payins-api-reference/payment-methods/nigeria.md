# Nigeria

### Payment Methods Available

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
      <th style="text-align:left"><b>Allowed Flows</b>
      </th>
      <th style="text-align:left"><b>Logos</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>CARD</code>
      </td>
      <td style="text-align:left">Visa</td>
      <td style="text-align:left"><code>CARD</code>
      </td>
      <td style="text-align:left"><code>VI</code>
      </td>
      <td style="text-align:left">Credit Card</td>
      <td style="text-align:left">
        <p><code>DIRECT</code>
        </p>
        <p><code>REDIRECT</code>
        </p>
      </td>
      <td style="text-align:left">&#x200B;<a href="https://pay.dlocal.com/views/2.0/images/payments/VI.png">https://pay.dlocal.com/views/2.0/images/payments/VI.png</a>&#x200B;</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>CARD</code>
      </td>
      <td style="text-align:left">Mastercard</td>
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
      <td style="text-align:left">&#x200B;https://pay.dlocal.com/views/2.0/images/payments/VD.png&#x200B;</td>
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
      <td style="text-align:left">&#x200B;https://pay.dlocal.com/views/2.0/images/payments/MD.png&#x200B;</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>CARD</code>
      </td>
      <td style="text-align:left">Verve</td>
      <td style="text-align:left"><code>CARD</code>
      </td>
      <td style="text-align:left"><code>VE</code>
      </td>
      <td style="text-align:left">Debit Card</td>
      <td style="text-align:left">
        <p><code>DIRECT</code>
        </p>
        <p><code>REDIRECT</code>
        </p>
      </td>
      <td style="text-align:left">&#x200B;https://pay.dlocal.com/views/2.0/images/payments/VE.png&#x200B;</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>IO</code>
      </td>
      <td style="text-align:left">TEF</td>
      <td style="text-align:left"><code>BANK_TRANSFER</code>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Bank transfer</td>
      <td style="text-align:left"><code>REDIRECT</code>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><code>IO</code>
      </td>
      <td style="text-align:left">Okra</td>
      <td style="text-align:left"><code>BANK_TRANSFER</code>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Direct Debit</td>
      <td style="text-align:left"><code>REDIRECT</code>
      </td>
      <td style="text-align:left"><a href="https://static.dlocal.com/images/providers/Okra.png">https://static.dlocal.com/images/providers/Okra.png</a>
      </td>
    </tr>
  </tbody>
</table>

### Okra \(Direct Debit\) Examples

{% tabs %}
{% tab title="Request Example" %}
```text
{
    "amount": 10,
    "currency": "NGN",
    "country": "NG",
    "payment_method_id": "IO",
    "payment_method_flow": "REDIRECT",
    "payer": {
        "name": "#RANDOMNAME",
        "email": "agarcia@dlocal.com",
        "phone": "+80000000011",
        "document": "123455",
        "document_type": "CI",
        "address": {
            "country": "MX",
            "state": "Santa Catarina",
            "city": "Florianopolis",
            "zip_code": "88058",
            "street": "Rodovia Armando Calil Bulos",
            "number": "5940"
        }
    },
    "order_id": "#RANDOMUUID",
    "description": "USE_TEST_CURRENCY",
    "notification_url": "http://conductor.sandbox.internal/robot-server/rest/generic/notification/new"
}
```
{% endtab %}

{% tab title="Response Example" %}
```text
{
    "id": "D-4-80fc030b-f0a1-4252-9f3e-aa4a0cbae4b6",
    "amount": 10,
    "currency": "NGN",
    "payment_method_id": "IO",
    "payment_method_type": "BANK_TRANSFER",
    "payment_method_flow": "REDIRECT",
    "country": "NG",
    "created_date": "2021-03-11T16:23:13.000+0000",
    "status": "PENDING",
    "status_detail": "The payment is pending.",
    "status_code": "100",
    "order_id": "c54f7498-e056-43b1-876c-880a825189f4",
    "description": "USE_TEST_CURRENCY",
    "notification_url": "http://conductor.sandbox.internal/robot-server/rest/generic/notification/new",
    "redirect_url": "https://sandbox.dlocal.com/collect/pay/pay/M-a66d9d38-ec9d-43f4-a643-8ca870149eb3?xtid=CATH-ST-1615479793-1962654176"
}
```
{% endtab %}
{% endtabs %}

