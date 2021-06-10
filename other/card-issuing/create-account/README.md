# Create account

This page explains how to create accounts and account owners. Both are created together and are related in a 1to1 structure.

An account-owner is the basic account structure that is needed to hold funds, make and receive payments and issue cards.

To create an account you will need to provide owner's KYC details such as Full Name, Address, Tax ID document.

Each account will have a unique `account_id` that will be needed to transact, query, transfer, top-up and manage. This `account_id` is provided on API call response. You must store this value.

The flow to register users and create account is:

1. Create account-owner
2. Upload KYC documents. _Required only for Brazil._
3. Sent OTP Codes \(Email / Phone Number\). _Required only for Colombia._

You will then receive a final status once the account is approved. 

​

