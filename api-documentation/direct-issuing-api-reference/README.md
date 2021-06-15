# Direct Issuing API Reference

### Set up

Follow these 4 easy steps to start with your integration setup:

1. Refer to the flows page to get a full and general picture of the services included in this API

{% page-ref page="issuing-flows.md" %}

2. Review the Environments page to see the references for our Production and Sandbox environments. Both of the will work with the same requests listed in the upcoming pages:

{% page-ref page="environments.md" %}

3. Make sure you set up the call headers as detailed in the Security page:

{% page-ref page="security.md" %}

4. Move on to the detailed pages for the services offered by this API. In order to start creating user accounts, you'll be using 3 main group of services: 

1. Creating and managing user's accounts
2. Sending and managing funds for those accounts 
3. Issuing pre-paid cards, linked to the account balances

### Create and manage user accounts

The solution requires you to create an account for each user you want to credit funds to. Our API allows you to easily create and manage these accounts, which includes enabling or disabling them, or retrieving relevant account information such as the balance, status or the owner's information. Follow the links bellow to learn more about these services: ​

{% page-ref page="create-account/" %}

{% page-ref page="manage-accounts/" %}

### Manage Funding

Once the account is created, you can easily transfer funds to top up the user accounts in local currency. You also get access to a wide variety of information retrieving services, including transfers information, Retrieving account's balance, and a transaction history.

{% page-ref page="managing-funds/" %}

### Create and issue cards

Direct Issuing allows you to issue virtual and physical pre-paid cards linked to the user's account. The user will be able to use the cards to pay for anything online, but also to pay offline with the physical card. Refer to this section to learn more about the card creation service:

{% page-ref page="create-and-issue-card/" %}



