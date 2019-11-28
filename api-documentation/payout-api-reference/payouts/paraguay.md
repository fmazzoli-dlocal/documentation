# Paraguay

### Mandatory parameters

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **password** | 32 chars |
| **external\_id** | Max. 100 chars |
| **document\_type** | See document validations [here](paraguay.md#documents-validation) |
| **document\_id** | See document validations [here](paraguay.md#documents-validation) |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | PA |
| **currency** | PYG or USD or EUR |
| **bank\_code** | BIC code |
| **bank\_account** | See bank's account validations [here.](paraguay.md#bank-accounts-validations) |
| **amount** | Max. 2 decimal numbers |

### Example request

```text

```

### Document's validation

| Validation | Name | Length | Type | Verification digit |
| :--- | :--- | :--- | :--- | :--- |
| Document | CI | 7 | numeric | N/A |
| Document | RUC | 8 | numeric | CI + validation algorithm |

### Bank account's validations

| Validation | Name | Length | Type | Verification digit |
| :--- | :--- | :--- | :--- | :--- |
| Bank account | SIPAP | 16 | numeric | N/A |

{% hint style="info" %}
If the account number has less than 16 digits, zeros should be added to the left side, so as to complete the mandatory length
{% endhint %}

