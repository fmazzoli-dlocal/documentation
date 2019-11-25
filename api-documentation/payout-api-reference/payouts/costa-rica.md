# Costa Rica

## Mandatory parameters

| **Mandatory parameter** | **Description** |
| :--- | :--- |
| **login** | 32 chars |
| **password** | 32 chars |
| **external\_id** | Max. 100 chars |
| **document\_id** | See document's validations [here](costa-rica.md#documents-validations) |
| **document\_type** | See document's validations [here](costa-rica.md#documents-validations) |
| **beneficiary\_name** | Max. 100 chars |
| **beneficiary\_lastname** | Max. 100 chars |
| **country** | CR |
| **bank\_account** | See bank account's validations [here](costa-rica.md#bank-account-validations) |
| **amount** | Max. 2 decimal numbers |
| **address** | Max. 200 chars |

## Example request

```text

```

## Document's validations

| Validation | Name | Length | Type | Verification digit | Example |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Document | CI | 9 | numeric | No | 123456789 |
| Document | CJ | 10 | numeric | No | 1234567890 |
| Document | CR | 11 to 22 | numeric | No | 1234567890155566 |

## Bank account validations

| _Validation_ | Name | Length | Type | Verification digit | Example |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Bank account | IBAN | 17 | numeric | Apply verification algorithm | 12345678912345678 |



