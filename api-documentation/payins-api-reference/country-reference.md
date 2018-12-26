# Country Reference

## Documents

Bellow are the allow documents for each country that need to be entered in the [Payer Object. ](payments/#the-payer-object)

Some countries might require more than one document \(eg: India\). In that case, other required documents need to be included in additional `document[#]` parameters.

{% tabs %}
{% tab title="Example Payer Object: Brazil" %}
```yaml
{
"name" : "Thiago Alcántara",
"email" : "thiago@example.com",
"document" : "42243309114", ->CPF
}
```
{% endtab %}

{% tab title="Example Payer Object: India" %}
```yaml
{
"name" : "Parag Chilimbi",
"email" : "parag@example.com",
"document" : "548550008000", ->Aadhar
"document2" : "EHFGA5967A", ->PAN
}
```
{% endtab %}
{% endtabs %}

<table>
  <thead>
    <tr>
      <th style="text-align:left">Country</th>
      <th style="text-align:left">Document(s)</th>
      <th style="text-align:left">Allowed Format</th>
      <th style="text-align:left">Field in Payer Object</th>
      <th style="text-align:left">Required</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Argentina</td>
      <td style="text-align:left">DNI or CUIT</td>
      <td style="text-align:left">between 7 to 9, or 11 digits</td>
      <td style="text-align:left"><code>document</code>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Brazil</td>
      <td style="text-align:left">CPF or CNPJ</td>
      <td style="text-align:left">between 11 to 14 digits
        <br />full CPF validation</td>
      <td style="text-align:left"><code>document</code>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Chile</td>
      <td style="text-align:left">CI/RUT</td>
      <td style="text-align:left">between 8 to 9 digits</td>
      <td style="text-align:left"><code>document</code>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">China</td>
      <td style="text-align:left">
        <p>公民身份号码</p>
        <p>(citizen ID number)</p>
      </td>
      <td style="text-align:left">between 5 to 20 digits</td>
      <td style="text-align:left"><code>document</code>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Colombia</td>
      <td style="text-align:left">CC</td>
      <td style="text-align:left">between 6 to 10 digits</td>
      <td style="text-align:left"><code>document</code>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">India</td>
      <td style="text-align:left">Aadhaar</td>
      <td style="text-align:left">
        <p>12 digits</p>
        <p>full Aadhaar validation</p>
      </td>
      <td style="text-align:left"><code>document</code>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">PAN</td>
      <td style="text-align:left">
        <p>10 characters
          <br />(5 letters, 4 numbers, 1 letter/number)</p>
        <p>full PAN validation</p>
      </td>
      <td style="text-align:left"><code>document2</code>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Mexico</td>
      <td style="text-align:left">CURP</td>
      <td style="text-align:left">between 10 to 18 digits</td>
      <td style="text-align:left"><code>document</code>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Morocco</td>
      <td style="text-align:left">CNIE</td>
      <td style="text-align:left">between 5 to 20 digits</td>
      <td style="text-align:left"><code>document</code>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Paraguay</td>
      <td style="text-align:left">CI</td>
      <td style="text-align:left">between 5 to 20 digits</td>
      <td style="text-align:left"><code>document</code>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Peru</td>
      <td style="text-align:left">DNI</td>
      <td style="text-align:left">between 8 to 9 digits</td>
      <td style="text-align:left"><code>document</code>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Turkey</td>
      <td style="text-align:left">T.C. Kimlik No.</td>
      <td style="text-align:left">between 5 to 20 digits</td>
      <td style="text-align:left"><code>document</code>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Uruguay</td>
      <td style="text-align:left">CI</td>
      <td style="text-align:left">between 6 to 8 digits</td>
      <td style="text-align:left"><code>document</code>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
  </tbody>
</table>