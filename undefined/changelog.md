# Changelog

## Changes from v2.0

* **New method for capturing authorizations:** While Authorizations are created the same way as in v2.0, capturing that Authorization now looks more similar as creating a payment. The main advantages for this are:
  * Support for multiple partial captures: Availability depends on region, please contact your Technical Account Manager for more details. 
  * You can now add an `order_id` to each individual Capture, meaning that you can add your own external reference to each of them. Previously only the Authorization had this feature.
  * Refunds are now applied to individual Captures, and not to the Authorization.
* Request headers now need to include API version \(eg: X-Version = 2.1\). Learn more [here](../api-documentation/payins-api-reference/security.md#headers).
* Removed 'Credit Card Payment Operations' page, and instead replaced it with multiple sub-pages under '[Credit Card Payments](../api-documentation/payins-api-reference/payments/credit-card-payments/)':
  * [Authorization and Capture](../api-documentation/payins-api-reference/payments/credit-card-payments/authorization-and-capture.md)
  * [Chargebacks](../api-documentation/payins-api-reference/payments/credit-card-payments/chargebacks.md)
  * [3D-Secure](../api-documentation/payins-api-reference/payments/credit-card-payments/3d-secure.md)

