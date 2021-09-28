---
description: See all the information for the creation of an account for Mexico.
---

# Mexico

## Flow

![Flow for creation of Mexican &#x200B;accounts.](../../../../.gitbook/assets/image%20%2831%29.png)

## Mandatory parameters

{% tabs %}
{% tab title="Owner object" %}
| Property | Description |
| :--- | :--- |
| `first_name` | Owner's first name.  |
| `last_names` | Owner's complete last names. |
| `birth_date` | Owner's birth date. Users must be over 18 years old.  |
| `email` | Owner's email. |
| `phone_number` | Owner's cellphone number.  |
| `document` | Owner’s personal identification number.  |
| `document_type` | Owner's personal [identification type](mexico.md#document-type). |
| `gender` | M or F. |
| `marital_status` | Check the [marital status table](mexico.md#marital-status) below for more details. |
| `ip_address` | Owner's IP address.  |
{% endtab %}

{% tab title="Address object" %}
Find more details of the state and city fields on ****[Address Information](mexico.md#address-information)**.**

| Property | **Description** |
| :--- | :--- |
| `country` | Owner's country code. ISO 3166-1 alpha-2-code. \(CO\) |
| `city` | Owner's address city code. |
| `state` | Owner's address state code. |
| `street` | Owner's address street. |
| `zip_code` | Owner's address [ZIP code](https://docs.google.com/spreadsheets/d/1EW7JI-B814GAdULTr4njyBUulDvTTQ5dM_M2kD5AAkw/edit?usp=sharing). |
{% endtab %}

{% tab title="Notifications" %}
| Property | Description |
| :--- | :--- |
| `notification_url` | Notification to receive change status webhooks. |
{% endtab %}
{% endtabs %}

## Document type

| Type | Description |
| :--- | :--- |
| IFE | Credencial Instituto Federal Electoral |
| INE | Instituto Nacional Electoral |
| PAS | Pasaporte |

## Marital status

| Status | Description |
| :--- | :--- |
| S | Single |
| M | Married |
| W | Widowed |
| D | Divorced |

## Address information

### **States** 

[Download the table in xlsx version](https://docs.google.com/spreadsheets/d/12DUNd4VFPfsszs5x4ZRyk3xJJVM-5dgJphhA437Uxkg/edit?usp=sharing).

<table>
  <thead>
    <tr>
      <th style="text-align:left">Code</th>
      <th style="text-align:left">Name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">TAMAULIPAS</td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">TLAXCALA</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>3</p>
        <p>
          <br />
        </p>
      </td>
      <td style="text-align:left">VERACRUZ</td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">YUCATAN</td>
    </tr>
    <tr>
      <td style="text-align:left">5</td>
      <td style="text-align:left">ZACATECAS</td>
    </tr>
    <tr>
      <td style="text-align:left">6</td>
      <td style="text-align:left">BAJA CALIFORNIA NORTE</td>
    </tr>
    <tr>
      <td style="text-align:left">A</td>
      <td style="text-align:left">AGUASCALIENTES</td>
    </tr>
    <tr>
      <td style="text-align:left">B</td>
      <td style="text-align:left">BAJA CALIFORNIA SUR</td>
    </tr>
    <tr>
      <td style="text-align:left">C</td>
      <td style="text-align:left">CAMPECHE</td>
    </tr>
    <tr>
      <td style="text-align:left">D</td>
      <td style="text-align:left">CHIAPAS</td>
    </tr>
    <tr>
      <td style="text-align:left">E</td>
      <td style="text-align:left">CHIHUAHUA</td>
    </tr>
    <tr>
      <td style="text-align:left">F</td>
      <td style="text-align:left">COAHUILA</td>
    </tr>
    <tr>
      <td style="text-align:left">G</td>
      <td style="text-align:left">COLIMA</td>
    </tr>
    <tr>
      <td style="text-align:left">H</td>
      <td style="text-align:left">DISTRITO FEDERAL</td>
    </tr>
    <tr>
      <td style="text-align:left">I</td>
      <td style="text-align:left">DURANGO</td>
    </tr>
    <tr>
      <td style="text-align:left">J</td>
      <td style="text-align:left">ESTADO DE MEXICO</td>
    </tr>
    <tr>
      <td style="text-align:left">K</td>
      <td style="text-align:left">GUANAJUATO</td>
    </tr>
    <tr>
      <td style="text-align:left">L</td>
      <td style="text-align:left">GUERRERO</td>
    </tr>
    <tr>
      <td style="text-align:left">M</td>
      <td style="text-align:left">HIDALGO</td>
    </tr>
    <tr>
      <td style="text-align:left">N</td>
      <td style="text-align:left">JALISCO</td>
    </tr>
    <tr>
      <td style="text-align:left">O</td>
      <td style="text-align:left">MICHOACAN</td>
    </tr>
    <tr>
      <td style="text-align:left">P</td>
      <td style="text-align:left">MORELOS</td>
    </tr>
    <tr>
      <td style="text-align:left">Q</td>
      <td style="text-align:left">NAYARIT</td>
    </tr>
    <tr>
      <td style="text-align:left">R</td>
      <td style="text-align:left">NUEVO LEON</td>
    </tr>
    <tr>
      <td style="text-align:left">S</td>
      <td style="text-align:left">OAXACA</td>
    </tr>
    <tr>
      <td style="text-align:left">T</td>
      <td style="text-align:left">PUEBLA</td>
    </tr>
    <tr>
      <td style="text-align:left">U</td>
      <td style="text-align:left">QUERETARO</td>
    </tr>
    <tr>
      <td style="text-align:left">V</td>
      <td style="text-align:left">QUINTANA ROO</td>
    </tr>
    <tr>
      <td style="text-align:left">W</td>
      <td style="text-align:left">SAN LUIS POTOSI</td>
    </tr>
    <tr>
      <td style="text-align:left">X</td>
      <td style="text-align:left">SINALOA</td>
    </tr>
    <tr>
      <td style="text-align:left">Y</td>
      <td style="text-align:left">SONORA</td>
    </tr>
    <tr>
      <td style="text-align:left">Z</td>
      <td style="text-align:left">TABASCO</td>
    </tr>
  </tbody>
</table>

### **Cities**

To find the City's ID, [download the table on xlsx version](https://docs.google.com/spreadsheets/d/1jbmpSdACKWHGcytsmW14OnZGuULNweKRAW-weLINBc0/edit?usp=sharing). 

