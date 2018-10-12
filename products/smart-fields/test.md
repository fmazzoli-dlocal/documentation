### `dlocal.createInstallmentsPlan(field, amount, currency)`

Use `dlocal.createInstallmentsPlan(field, amount, currency)`to specify an installment plan, to guarantee the surcharge per installment that will be charged.

```javascript
dlocal.createInstallmentsPlan(card, amount, currency)
.then(function(result) {
  // Handle result.installments
}
.catch(function(result) {
  // Handle result.error
}););
```

{% tabs %}
{% tab title="Installments Arguments!" %}
<table>
  <thead>
    <tr>
      <th style="text-align:left">Parameter</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>field</code>
      </td>
      <td style="text-align:left">SmartField</td>
      <td style="text-align:left">
        <p></p>
        <p></p>
        <p>The Smart Field you wish to create the installments plan, if you are not
          using a <code>card</code> Field we recommend to use <code>number</code> Field
          to create installments, but any of the Fields will work.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>amount</code>
      </td>
      <td style="text-align:left">Positive Float</td>
      <td style="text-align:left">The amount of the installments plan.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>currency</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The currency of the installments plan.</td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="Installments Plan Object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | String | The installments plan id. |
| `country` | String | The country of the installments plan \(this is the same you specified when you created the field\). |
| `currency` | String | The currency of the installments plan. |
| `bin` | String | The credit card bin. |
| `amount` | Positive Float | The amount of the installments plan. |
| `installments` | ​[Installment Object](https://docs.dlocal.com/api-documentation/payins-api-reference/installments#the-installment-object)\[ \] | The installments plan information |
{% endtab %}

{% tab title="Installment Object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | String | The installment id. |
| `installment_amount` | Positive Float | Installment amount. |
| `total_amount` | Positive Float | Installments total amount. |
| `installments` | Integer | Number of installments. |
{% endtab %}

{% tab title="Example Installments Plan Object" %}
```javascript
{
    "id" : "INS54434",
    "country" : "BR",
    "currency" : "BRL",
    "bin" : "435921",
    "amount": 1500,
    "installments" : [
        {
            "id" : "INS54434-3",
            "installment_amount" : 550,
            "installments" : 3,
            "total_amount" : 1650
        },
        {
            "id" : "INS54434-6",
            "installment_amount" : 350,
            "installments" : 6,
            "total_amount" : 2100
        },
        {
            "id" : "INS54434-8",
            "installment_amount" : 250,
            "installments" : 12,
            "total_amount" : 3000
        }
    ]
}
```
{% endtab %}
{% endtabs %}

## The Fields Object

* \*\*\*\*[**fields.create\(\)**](dlocal.js-reference.md#fields-create-type-options)\*\*\*\*

### `fields.create(type, options)`

```javascript
var card = fields.create('card');
```

This method creates an instance of a specific Smart Field. It takes the`type` of Smart Field to create as well as an `options` object.

### **Smart Field Types**

| **Type** | **Description** |
| :--- | :--- |
| `card` | A flexible single-line input that collects cardNumber, cardExpiry and cardCvc. **\(Recommended\)** |
| `pan` | The card‘s number.  |
| `expiration` | The card‘s expiration date.  |
| `cvv` | The card‘s CVC number.  |

{% hint style="info" %}
We highly recommend to use the `card` Field, as it provides a better user experience.
{% endhint %}

### **Field Options**

All Smart Fields accept a common set of options, and then some Field-specific options.
