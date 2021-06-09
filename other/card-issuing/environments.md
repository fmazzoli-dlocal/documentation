# Environments

## Get your API credentials  <a id="get-your-api-credentials"></a>

All dLocal API requests require API credentials to verify the call is being made through a valid dLocal account.

### Sandbox

There is a test environment available for integration development and testing, which simulates most of the requests and transaction types available in the platform. You can use this environment to ensure your requests are handled accordingly. 

The base URL for development is: [**https://issuing-api.dlocal-sbox.com** ](https://issuing-api.dlocal-sbox.com)\*\*\*\*

{% hint style="info" %}
_**Please note that in the test environment, no transactions will actually be processed.**_
{% endhint %}

## **Testing Issuing’s endpoints** <a id="testing-issuings-endpoints"></a>

This endpoint changes the status of the account/card/transfer in the sandbox environment and notifies the merchant of the status changes. 

To change the **account status:**

**Url**: [https://issuing-api.dlocal-sbox.com/issuing/sandbox-tools/accounts](https://issuing-api.dlocal-sbox.com/issuing/sandbox-tools/accounts)  
**Header requirements**: X-Login, X-Trans-Key, X-Date y X-Key=**sandbox-tool-kit-5678023**  
**Body**:

```text
{
     "account_id":"ID",
     "status":"ACTIVE|INACTIVE|REJECTED"
}
```

To change the **card status:**:  
**Url**: [https://issuing-api.dlocal-sbox.com/issuing/sandbox-tools/cards](https://issuing-api.dlocal-sbox.com/issuing/sandbox-tools/cards)  
**Header requirements**: X-Login, X-Trans-Key, X-Date y X-Key=**sandbox-tool-kit-5678023**  
**Body**:

```text
{
     "card_id":"ID",
     "status":"ACTIVE|INACTIVE|REJECTED"
}
```

To change the **transfer status \(disbursment\)**:  
**Url**: [https://issuing-api.dlocal-sbox.com/issuing/sandbox-tools/transfer](https://issuing-api.dlocal-sbox.com/issuing/sandbox-tools/transfer)  
**Header requirements**: X-Login, X-Trans-Key, X-Date y X-Key=**sandbox-tool-kit-5678023**  
**Body**:

```text
{
     "transaction_id":"ID",
     "status":"APPROVED|REJECTED"
}
```

### **Production**

After the testing phase is successful, you are ready to go live in the production environment.

The base URL for production is: [**https://issuing-api.dlocal.com**](https://issuing-api.dlocal.com)**​**

​

