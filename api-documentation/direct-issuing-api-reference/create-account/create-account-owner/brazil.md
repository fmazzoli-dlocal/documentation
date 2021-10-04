---
description: See all the information for the creation of an account for Brazil.
---

# Brazil

## Flow

![Flow for creation of Brazilian accounts.](../../../../.gitbook/assets/image%20%2833%29.png)

## Mandatory parameters

{% tabs %}
{% tab title="Owner object" %}
| Property | Description |
| :--- | :--- |
| `first_name` | Owner's first name.  |
| `last_names` | Owner's complete last names. |
| `birth_date` | Owner's birth date.  |
| `email` | Owner's email. |
| `phone_number` | Owner's cellphone number. Include DDD. |
| `document` | Owner’s personal [identification number](brazil.md#document-type).  |
| `mother_name` | Mother full name.  |
| `gender` | M or F. |
| `marital_status` | Check the [marital status table](brazil.md#marital-status) below for more details. |
| `ip_address` | Owner's IP address. |
{% endtab %}

{% tab title="Address object" %}
Find more details of the state and city fields on ****[Address Information](brazil.md#address-information)**.**

| Property | Description |
| :--- | :--- |
| `country` | Owner's country code. ISO 3166-1 alpha-2-code. \(CO\) |
| `city` | Owner's address city code.  |
| `state` | Owner's address state code. |
| `street` | Owner's address street. |
| `house_number` | Owner's house number \(floor, apartment\). |
| `zip_code` | Owner's address ZIP code. |
| `neighbourhood` | Neighbourhood or district. |
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
| RG | Registro Geral |
| CNH | Carteira Nacional de Habilitação |
| CPF | Cadastro de Pessoa Física |

## Marital status

| Status | Description |
| :--- | :--- |
| S | Single |
| M | Married |
| W | Widowed |
| D | Divorced |

## Address information

### **States** 

[Download the table in xlsx version.](https://docs.google.com/spreadsheets/d/1vjuMiNAEqM75l0QbRIbg6CRD1lxuQlzY/edit?usp=sharing&ouid=111924045272314592561&rtpof=true&sd=true)

| Code | Name |
| :--- | :--- |
| AC | Acre |
| AL | Alagoas |
| AP | Amapá |
| AM | Amazonas |
| BA | Bahia |
| CE | Ceará |
| DF | Distrito Federal |
| ES | Espírito Santo |
| GO | Goiás |
| MA | Maranhão |
| MT | Mato Grosso |
| MS | Mato Grosso do Sul |
| MG | Minas Gerais |
| PA | Pará |
| PB | Paraíba |
| PR | Paraná |
| PE | Pernambuco |
| PI | Piauí |
| RN | Rio Grande do Norte |
| RS | Rio Grande do Sul |
| RJ | Rio de Janeiro |
| RO | Rondônia |
| RR | Roraima |
| SC | Santa Catarina |
| SP | São Paulo |
| SE | Sergipe |
| TO | Tocantins |

### **Cities**

To find the City's ID, [download the table on xlsx version](https://docs.google.com/spreadsheets/d/12s35bUqttJZWfQSeSn6nIClZnz1BdAcz/edit?usp=sharing&ouid=111924045272314592561&rtpof=true&sd=true). 

