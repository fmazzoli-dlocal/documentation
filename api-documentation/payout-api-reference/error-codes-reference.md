# API codes

This section includes a description of every API code used in the Payouts API, check below for:

* [Payout status](error-codes-reference.md#payout-status) - The possible status taken by each payout
* [Error codes range](error-codes-reference.md#error-codes-range) - The error code shown when a payout fails
* [Purpose codes reference](error-codes-reference.md#purpose-codes-reference) - To comply with bank's regulations

## Payout status

The Payout status can take one of the following values:

| Code | Description | Description |
| :--- | :--- | :--- |
| 0 | Pending | The payout is received to be processed in the next cut off |
| 1 | Completed | The payout was completed |
| 2 | Cancelled | The payout was cancelled |
| 3 | Rejected | The payout was rejected by the bank |
| 4 | Delivered | The payout is being processed by the bank. |
| 5 | On hold | The payout is on hold by the merchant or awaiting for further legal information to be processed |

## Error codes range

| Description | Code range |
| :--- | :--- |
| Syntax validation in parameter/s | 3xx |
| Merchant identification validation | 4xx |
| Business logic validation | 5xx |
| Semantic validation in parameter/s | 6xx |
| Transactional error | 7xx |
| Rejection error \(only API Version 2.0\) | 8xx |

Different error codes types can be seen below:

* [Syntax codes reference](error-codes-reference.md#syntax-codes-reference)
* [Merchant identification validation](error-codes-reference.md#merchant-identification-validation)
* [Business logic validation](error-codes-reference.md#business-logic-validation)
* [Transactional error](error-codes-reference.md#transactional-error)
* [Rejection error](error-codes-reference.md#rejection-error)

### Syntax codes reference

| Code | Description |
| :--- | :--- |
| 300 | Invalid params + \[param name\] + \[reason\] |
| 301 | Empty params + \[param name\] |
| 302 | Invalid control string |
| 303 | Invalid bank code |

### Merchant identification validation

<table>
  <thead>
    <tr>
      <th style="text-align:left">Code</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">401</td>
      <td style="text-align:left">Invalid credentials</td>
    </tr>
    <tr>
      <td style="text-align:left">402</td>
      <td style="text-align:left">
        <p>Unregistered IP address</p>
        <p>(register is in merchant&apos;s panel)</p>
      </td>
    </tr>
  </tbody>
</table>### Business logic validation

| Code | Description |
| :--- | :--- |
| 507 | Country not found for payouts |
| 508 | Limit exceeded + \[limit name\] |
| 509 | Payout not found with this ID |
| 510 | Invalid status: payout is not Pending |
| 511 | External ID already used |
| 514 | Insufficient funds |

### Transactional error

| Code | Description |
| :--- | :--- |
| 702 | Could not cancel the payout |
| 703 | Could not make the payout |

### Rejection error

| Code | Description |
| :--- | :--- |
| 800 | 'ERROR\_ACCOUNT\_INCORRECT' |
| 801 | 'ERROR\_ACCOUNT\_CLOSED' |
| 802 | 'ERROR\_AMOUNT\_INCORRECT' |
| 803 | 'ERROR\_BANK\_INVALID' |
| 804 | 'ERROR\_BANK\_BRANCH\_INCORRECT' |
| 805 | 'ERROR\_BENEFICIARY\_DOCUMENT\_ID\_INVALID' |
| 806 | 'ERROR\_BENEFICIARY\_NAME\_INCORRECT' |
| 807 | 'ERROR\_REJECTED\_BY\_BANK' |
| 808 | 'ERROR\_OTHER' |
| 809 | ERROR\_ACCOUNT\_TYPE\_INCORRECT |
| 810 | ERROR\_ACCOUNT\_NOT\_MATCH\_BENEFICIARY\_DOCUMENT |
| 811 | ERROR\_ACCOUNT\_NOT\_MATCH\_BENEFICIARY\_NAME |
| 812 | ERROR\_ACCOUNT\_NOT\_ACCEPT\_TRANSFERS |
| 813 | ERROR\_BENEFICARY\_DOCUMENT\_NOT\_MATCH\_NAME |
| 814 | ERROR\_ACCOUNT\_OF\_OTHER\_CURRENCY |

## Purpose codes reference

Some countries' bank compliance processes require you to specify each payment's purpose:

| **Code** | **Description** |
| :--- | :--- |
| EPFAMT | Family maintenance |
| ISMDCS | Payment for medical care services |
| ISSTDY | Payment of study/tuition costs |
| ISCHAR | Payment for charity reasons |
| EPPROP | Payment of property purchase |
| EPSHAR | Payment of shares |
| EPIVST | Payment of an investment |
| ISUBIL | Payment to common utility provider |
| ISTAXS | Payment of taxes |
| EPTOUR | Tourism |
| ISSAVG | Payment to savings/retirement account |
| ISPENS | Pension payment |
| ISPAYR | Payment of payroll |
| ISGDDS | Purchase sale of goods |
| ISSUPP | Supplier payment |
| EPREMT | Remittances |
| ISSCVE | Purchase sale of services |

