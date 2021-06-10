# Transfer Funds

​This function allows transfers from account. It can be used for:

1. Transferring funds from merchant account to user account \(credit funds to user\).
2. Payouts to bank accounts. **\(Soon\)**

{% api-method method="post" host="https://sandbox.dlocal.com" path="/issuing/transfers" %}
{% api-method-summary %}
Transfer Funds
{% endapi-method-summary %}

{% api-method-description %}
This function allows to transfer funds. Flows can be user to user, merchant to user, user to merchant, or user to bank account.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="notification\_url" type="string" required=true %}
Notification to recibe change status webhooks 
{% endapi-method-parameter %}

{% api-method-parameter name="transfer\_type" type="string" required=true %}
enum\('disbursement'\)
{% endapi-method-parameter %}

{% api-method-parameter name="beneficiary\_bank\_details" type="object" required=false %}
Bank account details. Required if destination\_account\_id is "external"
{% endapi-method-parameter %}

{% api-method-parameter name="currency" type="string" required=true %}
Transfer currency. Local currency
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="number" required=true %}
Amount to transfer
{% endapi-method-parameter %}

{% api-method-parameter name="transfer\_description" type="string" required=false %}
Optional message from user for transfer description.
{% endapi-method-parameter %}

{% api-method-parameter name="merchant\_reference" type="string" required=true %}
Merchant reference to identify transfer
{% endapi-method-parameter %}

{% api-method-parameter name="destination\_account\_id" type="string" required=false %}
Account id to credit funds. "external" if paying out to a bank account. **Required** for disbursements and payouts
{% endapi-method-parameter %}

{% api-method-parameter name="source\_account\_id" type="string" required=false %}
Account id from which to deduct funds. Can be merchant account. **Required** for payouts
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

### Beneficiary Bank Details Object

This object describes beneficiary bank details to payout. 

{% tabs %}
{% tab title="Beneficiary Bank Details Object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| beneficiary\_name | String | Beneficiary  Name |
| beneficiary\_lastname | String | Beneficiary Last Name |
| bank\_code | String | Beneficiary Bank code. See [here](https://docs.dlocal.com/api-documentation/payout-api-reference/payouts#country-requirements). |
| bank\_branch | String | Beneficiary Bank Branch code. See [here](https://docs.dlocal.com/api-documentation/payout-api-reference/payouts#country-requirements). |
| bank\_account | String | See bank account format [here](https://docs.dlocal.com/api-documentation/payout-api-reference/payouts#country-requirements) |
| account\_type | Char | "**C**" for currents, "**S**" for Savings |
{% endtab %}

{% tab title="Beneficiary  Bank Details Object Example" %}
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

#### Disbursement - Transfers from merchant to user account

Merchants can transfer \(credit\) funds to user account. This funds will be deducted from your balance and credited to user's wallet. In order to make such operation merchant needs to input users `account_id` on `destination_account_id` parameter and `transfer_type = "disbursement"`

#### Cashout-Payout to bank account

Users can transfer funds to a bank account account. This funds will be deducted from sender's account balance. In order to make such operation merchant needs to input sender's `account_id` on `source_account_id` parameter and `"external"` on `destination_account_id` parameter. Also,  `transfer_type = "payout"` ****and **Beneficiary Bank Details Object** must be provided.

#### Asynchronous Notifications

When there is a change of status in the transaction, we will send you a notification to the provided `notification_url` indicating `transfer_id` . You will need to call Get Transfer Information function to review this changes.

```text
{ 
  “transfer_id”:“ISGT-4-87270764b197409d9d2b29c8b43da784"
}
```

#### 

