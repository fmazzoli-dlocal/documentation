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

