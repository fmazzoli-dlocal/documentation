# Card Payments

For credit card payments you can use the card information only if you business is [Full PCI DSS compliant](https://docs.dlocal.com/solutions/payins#pci-compliance). Otherwise you need to securely collect the card information using [Smart Fields](https://docs.dlocal.com/products/smart-fields).   
For recurring payments, first [save the card](https://docs.dlocal.com/api-documentation/payins-api-reference/saving-cards#create-a-card), and then use the `card_id` to charge the card.

{% hint style="info" %}
**Important**: If you are making a payment **with credit card information** or a ****[**Google Pay**™ **token**](../google-pay.md), you need to use the following endpoint:   
h**ttps://api.dlocal.com/secure\_payments**

Card payments with a `card_id` or `token` should use the endpoint: **https://api.dlocal.com/payments**
{% endhint %}

{% page-ref page="../../api-documentation/payins-api-reference/payments/credit-card-payments/" %}

## Authorization and capture

Authorizing a card payment allows you to reserve funds in a customer's bank account, days before the actual payment occurs – for example when making hotel reservations or booking car rentals.

It's a two-step process. First you need to create an _Authorization_, and then you need to _Capture_ it.

{% page-ref page="../../api-documentation/payins-api-reference/payments/credit-card-payments/authorization-and-capture.md" %}

## Saving Cards

Stores a card's information on dLocal's servers, and returns a card\_id, that can be used to make payments later on

{% page-ref page="../../api-documentation/payins-api-reference/payments/credit-card-payments/saving-cards.md" %}

## Installments

When creating a card payment with installments, the Merchant will receive the **full amount** of the payment at settlement, with **no risks** involved.

To create a payment with installments, first you need to [create an Installments Plan](../../api-documentation/payins-api-reference/payments/credit-card-payments/installments.md#create-an-installments-plan), to guarantee the surcharge per installment that will be charged.

With the Installment Plan id \( `installments_id` \) and the number of installments, you can go ahead and create a payment with installments

{% page-ref page="../../api-documentation/payins-api-reference/payments/credit-card-payments/installments.md" %}

## Chargebacks

{% page-ref page="../../api-documentation/payins-api-reference/payments/credit-card-payments/chargebacks.md" %}

## 3D-Secure

In some regions 3D-Secure authentication might be mandatory.

{% page-ref page="../../api-documentation/payins-api-reference/payments/credit-card-payments/3d-secure.md" %}



