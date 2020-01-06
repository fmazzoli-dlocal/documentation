# Payouts API Reference

#### Introduction

The Payouts API allows you to deposit money in the bank account of a customer. The deposit will always be made in local currency. Once the transfer is confirmed by the bank, dLocal will send a notification to your merchant notification URL informing you of the result code of the transaction. This URL can be overridden by using the notification parameter for individual payout requests \(however note this new URL is only active for that particular payout\).

This section covers the basic concepts of the payment transaction types and the technical details of the Payouts API. It contains functional examples of the requests and important observations to be taken into account during integration.

### Content:

* [**Environments**](environments.md)\*\*\*\*
  * Testing phase vs. Live
* [**Security**](security.md)\*\*\*\*
  * How to make safe payment requests.
* [**Submit a payout**](payouts/)\*\*\*\*
  * Learn how to start making payouts.
* [**Check status**](check-status.md)\*\*\*\*
  * Check the payout's status.
* [**Cancel payout**](cancel-payout.md)\*\*\*\*
  * Cancel an unwanted payout
* \*\*\*\*[**Get exchange rate**](get-exchange-rate.md)\*\*\*\*
  * Consult the exchange rate of the given currency in relation to dollars
* [**Notification parameters**](notification-parameters.md)\*\*\*\*
  * Receiving a notification. When and how.
* \*\*\*\*[**API codes**](error-codes-reference.md)\*\*\*\*
  * Every code used in Payouts API, explained.



#### Get started with the Environments section of this documentation:

{% page-ref page="environments.md" %}





\*\*\*\*



