# Country Reference

In the table below you can find the `country` code and `currency` of the countries currently covered by dLocal. You can also find the `document` used in each country which needs to be entered in the [Payer Object. ](payments/#the-payer-object)

{% tabs %}
{% tab title="Example Payer Object: Brazil" %}
```yaml
{
"name" : "Thiago Alcántara",
"email" : "thiago@example.com",
"document" : "42243309114" //CPF
}
```
{% endtab %}
{% endtabs %}

<table>
  <thead>
    <tr>
      <th style="text-align:left">Country</th>
      <th style="text-align:left"><code>country</code> code</th>
      <th style="text-align:left"><code>currency</code> code</th>
      <th style="text-align:left"><code>document</code> name</th>
      <th style="text-align:left"><code>document</code> 
        <br />format</th>
      <th style="text-align:left"><code>document</code>required?</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Argentina</td>
      <td style="text-align:left"><code>AR</code>
      </td>
      <td style="text-align:left"><code>ARS</code>
      </td>
      <td style="text-align:left">DNI or CUIT</td>
      <td style="text-align:left">between 7 to 9, or 11 digits</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Bolivia</td>
      <td style="text-align:left"><code>BO</code>
      </td>
      <td style="text-align:left"><code>BOB</code>
      </td>
      <td style="text-align:left">CI</td>
      <td style="text-align:left">between 5 to 20 digits</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Brazil</td>
      <td style="text-align:left"><code>BR</code>
      </td>
      <td style="text-align:left"><code>BRL</code>
      </td>
      <td style="text-align:left">CPF or CNPJ</td>
      <td style="text-align:left">between 11 to 14 digits
        <br />full CPF validation</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Chile</td>
      <td style="text-align:left"><code>CL</code>
      </td>
      <td style="text-align:left"><code>CLP</code>
      </td>
      <td style="text-align:left">CI/RUT</td>
      <td style="text-align:left">between 8 to 9 digits</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">China</td>
      <td style="text-align:left"><code>CN</code>
      </td>
      <td style="text-align:left"><code>CNY</code>
      </td>
      <td style="text-align:left">
        <p>&#x516C;&#x6C11;&#x8EAB;&#x4EFD;&#x53F7;&#x7801;</p>
        <p>(citizen ID number)</p>
      </td>
      <td style="text-align:left">between 5 to 20 digits</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Colombia</td>
      <td style="text-align:left"><code>CO</code>
      </td>
      <td style="text-align:left"><code>COP</code>
      </td>
      <td style="text-align:left">CC</td>
      <td style="text-align:left">between 6 to 10 digits</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Ecuador</td>
      <td style="text-align:left"><code>EC</code>
      </td>
      <td style="text-align:left"><code>USD</code>
      </td>
      <td style="text-align:left">CI</td>
      <td style="text-align:left">between 5 to 20 digits</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">India</td>
      <td style="text-align:left"><code>IN</code>
      </td>
      <td style="text-align:left"><code>INR</code>
      </td>
      <td style="text-align:left">PAN</td>
      <td style="text-align:left">
        <p>10 characters
          <br />(5 letters, 4 numbers, 1 letter/number)</p>
        <p>full PAN validation</p>
      </td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Indonesia</td>
      <td style="text-align:left"><code>ID</code>
      </td>
      <td style="text-align:left"><code>IDR</code>
      </td>
      <td style="text-align:left">NIK</td>
      <td style="text-align:left">16 digits</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Mexico</td>
      <td style="text-align:left"><code>MX</code>
      </td>
      <td style="text-align:left"><code>MXN</code>
      </td>
      <td style="text-align:left">CURP</td>
      <td style="text-align:left">between 10 to 18 characters</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Morocco</td>
      <td style="text-align:left"><code>MA</code>
      </td>
      <td style="text-align:left"><code>MAD</code>
      </td>
      <td style="text-align:left">CNIE</td>
      <td style="text-align:left">between 5 to 20 digits</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Paraguay</td>
      <td style="text-align:left"><code>PY</code>
      </td>
      <td style="text-align:left"><code>PYG</code>
      </td>
      <td style="text-align:left">CI</td>
      <td style="text-align:left">between 5 to 20 digits</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Peru</td>
      <td style="text-align:left"><code>PE</code>
      </td>
      <td style="text-align:left"><code>PEN</code>
      </td>
      <td style="text-align:left">DNI</td>
      <td style="text-align:left">between 8 to 9 digits</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">South Africa</td>
      <td style="text-align:left"><code>ZA</code>
      </td>
      <td style="text-align:left"><code>ZAR</code>
      </td>
      <td style="text-align:left">ID</td>
      <td style="text-align:left">between 5 to 20 digits</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Turkey</td>
      <td style="text-align:left"><code>TR</code>
      </td>
      <td style="text-align:left"><code>TRY</code>
      </td>
      <td style="text-align:left">T.C. Kimlik No.</td>
      <td style="text-align:left">between 5 to 20 digits</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">Uruguay</td>
      <td style="text-align:left"><code>UY</code>
      </td>
      <td style="text-align:left"><code>UYU</code>
      </td>
      <td style="text-align:left">CI</td>
      <td style="text-align:left">between 6 to 8 digits</td>
      <td style="text-align:left">Yes</td>
    </tr>
  </tbody>
</table>