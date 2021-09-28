---
description: Learn how to create accounts and account owners.
---

# Create an account

## Accounts and accounts owners

The accounts and account owners are created together and are related in a 1to1 structure.

An _account-owner_ is the **basic account structure that is needed to hold funds, make and receive payments, and issue cards**.

To create an account you will need to provide the owner's KYC details such as full name, address, tax ID document.

Each account will have a unique `account_id` that will be needed to transact, query, transfer, top-up, and manage. This `account_id` is provided on API call response. You must store this value.

### Create an account

The flow to register users and create accounts is:

1. Create account-owner.
2. Upload KYC specific documents. **Required only for Brazil.**
3. Sent OTP Codes \(email and phone number\). **Required only for Colombia**_._

You will then receive a final status once the account is approved. 

​

