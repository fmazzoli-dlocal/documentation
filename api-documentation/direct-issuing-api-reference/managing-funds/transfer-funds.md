---
description: Learn how to transfer funds from an account.
---

# Transfer funds

​This function **allows transfers from an account**. It can be used for:

1. Transferring funds from merchant account to user account \(credit funds to a user\).
2. Payouts to bank accounts. _Coming soon._

{% api-method method="post" host="https://issuing-api.dlocal.com" path="/issuing/transfers" %}
{% api-method-summary %}
Transfer funds
{% endapi-method-summary %}

{% api-method-description %}
Flows can be user to user, merchant to user, user to merchant, or user to bank account.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="notification\_url" type="string" required=true %}
Notification to receive change status webhooks.
{% endapi-method-parameter %}

{% api-method-parameter name="transfer\_type" type="string" required=true %}
enum\('disbursement'\)
{% endapi-method-parameter %}

{% api-method-parameter name="beneficiary\_bank\_details" type="object" required=false %}
Bank account details. Required if destination\_account\_id is "external".
{% endapi-method-parameter %}

{% api-method-parameter name="currency" type="string" required=true %}
Transfer currency. Local currency.
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="number" required=true %}
Amount to transfer.
{% endapi-method-parameter %}

{% api-method-parameter name="transfer\_description" type="string" required=false %}
Optional message to the user for transfer description.
{% endapi-method-parameter %}

{% api-method-parameter name="merchant\_reference" type="string" required=true %}
Merchant reference to identify transfer.
{% endapi-method-parameter %}

{% api-method-parameter name="destination\_account\_id" type="string" required=false %}
Account ID to credit funds. "external" if paying out to a bank account. **Required for disbursements and payouts.**
{% endapi-method-parameter %}

{% api-method-parameter name="source\_account\_id" type="string" required=false %}
Account ID from which to deduct funds. Can be a merchant account. **Required for payouts.**
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "currency": "COP",
    "amount": 137,
    "transfer_description": "Transfer fund decription",
    "notification_url": "http://merchant.dlocal.com/notification",
    "merchant_reference": "y2x8ie3FEz",
    "destination_account_id": "ISGA-4-f0e70baca7784421a0e592f33d80f9ea",
    "transfer_type": "DISBURSEMENT",
    "date": "2021-03-09T17:02:16.55Z",
    "status": "PENDING",
    "transfer_id": "ISGT-4-795aad53aac54e649154791ac69cefad"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Beneficiary Bank Details object

This object describes beneficiary bank details to payout. 

{% tabs %}
{% tab title="Beneficiary Bank Details object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| `beneficiary_name` | String | Beneficiary name. |
| `beneficiary_lastname` | String | Beneficiary last name. |
| `bank_code` | String | [Beneficiary bank code](https://docs.dlocal.com/api-documentation/payout-api-reference/payouts#country-requirements). |
| `bank_branch` | String | [Beneficiary bank branch code](https://docs.dlocal.com/api-documentation/payout-api-reference/payouts#country-requirements). |
| `bank_account` | String | [Bank account](https://docs.dlocal.com/api-documentation/payout-api-reference/payouts#country-requirements). |
| `account_type` | Char | "C" for currents, "S" for savings. |
{% endtab %}

{% tab title="Example" %}
```text
{
    "beneficiary_name":"John",
    "beneficiary_lastname":"Miles",
    "bank_code":"341",
    "bank_branch":"0167",
    "bank_account":"12345-1",
    "account_type":"C",
}
```
{% endtab %}
{% endtabs %}

## Disbursement 

Merchants can transfer \(credit\) funds to a user account. These funds will be deducted from your balance and credited to the user's wallet. 

To make such operation, the merchant needs to input user's `account_id` on `destination_account_id` parameter and `transfer_type = "disbursement"`.

## Cashout - Payout to a bank account

Users can transfer funds to a bank account. These funds will be deducted from the sender's account balance.

To make such operation, the merchant needs to input sender's `account_id` on `source_account_id` parameter and `"external"` on `destination_account_id` parameter. Also,  `transfer_type = "payout"` ****and **Beneficiary Bank Details object must be provided.**

## Asynchronous notifications

When there is a change of status in the transaction, we will send you a notification to the provided `notification_url` indicating `transfer_id`. You will need to call [Get transfer information](get-transfer-information.md) function to review these changes.

```text
{ 
  “transfer_id”:“ISGT-4-87270764b197409d9d2b29c8b43da784"
}
```

