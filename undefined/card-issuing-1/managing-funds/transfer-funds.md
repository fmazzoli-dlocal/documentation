# Transfer Funds

​

This function allows transfers from account. It can be used for:

1. Transferring funds from merchant account to user account \(credit funds to user\).
2. Payouts to bank accounts. **\(Soon\)**

## Transfer Funds <a id="transfer-funds"></a>

https://sandbox.dlocal.com/issuing/transfers

This function allows to transfer funds. Flows can be user to user, merchant to user, user to merchant, or user to bank account.

Body Parameters

Notification to recibe change status webhooks

beneficiary\_bank\_details

optional

Bank account details. Required if destination\_account\_id is "external"

Transfer currency. Local currency

transfer\_description

optional

Optional message from user for transfer description.

merchant\_reference

required

Merchant reference to identify transfer

destination\_account\_id

optional

Account id to credit funds. "external" if paying out to a bank account. **Required** for disbursements and payouts

source\_account\_id

optional

Account id from which to deduct funds. Can be merchant account. **Required** for payouts

```text
{    "currency": "COP",    "amount": 137,    "transfer_description": "Transfer fund decription",    "notification_url": "http://merchant.dlocal.com/notification",    "merchant_reference": "y2x8ie3FEz",    "destination_account_id": "ISGA-4-f0e70baca7784421a0e592f33d80f9ea",    "transfer_type": "DISBURSEMENT",    "date": "2021-03-09T17:02:16.55Z",    "status": "PENDING",    "transfer_id": "ISGT-4-795aad53aac54e649154791ac69cefad"}
```

## Beneficiary Bank Details Object <a id="beneficiary-bank-details-object"></a>

This object describes beneficiary bank details to payout.

Beneficiary Bank Details Object

Beneficiary Bank Details Object Example

```text
{    "beneficiary_name":"John",    "beneficiary_lastname":"Miles",    "bank_code":"341",    "bank_branch":"0167",    "bank_account":"12345-1",    "account_type":"C",}
```

### Disbursement - Transfers from merchant to user account <a id="disbursement-transfers-from-merchant-to-user-account"></a>

Merchants can transfer \(credit\) funds to user account. This funds will be deducted from your balance and credited to user's wallet. In order to make such operation merchant needs to input users `account_id` on `destination_account_id` parameter and `transfer_type = "disbursement"`

### Cashout-Payout to bank account <a id="cashout-payout-to-bank-account"></a>

Users can transfer funds to a bank account account. This funds will be deducted from sender's account balance. In order to make such operation merchant needs to input sender's `account_id` on `source_account_id` parameter and `"external"` on `destination_account_id` parameter. Also, `transfer_type = "payout"` and **Beneficiary Bank Details Object** must be provided.

### Asynchronous Notifications <a id="asynchronous-notifications"></a>

When there is a change of status in the transaction, we will send you a notification to the provided `notification_url` indicating `transfer_id` . You will need to call Get Transfer Information function to review this changes.

```text
{   “transfer_id”:“ISGT-4-87270764b197409d9d2b29c8b43da784"}
```

### ​ <a id="undefined"></a>

