---
description: Send all the necessary information to validate the account.
---

# Upload KYC

This function is to send KYC files to provide the necessary documentation to validate the account.

{% hint style="warning" %}
Required only for ****Brazil.
{% endhint %}

{% api-method method="post" host="https://issuing-api.dlocal.com" path="/issuing/accounts/{account\_id}/images" %}
{% api-method-summary %}
Upload KYC
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="account\_id" type="string" required=true %}
Account ID provided when the account was created.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="file" type="string" required=true %}
Document image to upload.
{% endapi-method-parameter %}

{% api-method-parameter name="document\_type" type="string" required=true %}
"SELFIE", "RG" or "CNH". Max 1MB.
{% endapi-method-parameter %}

{% api-method-parameter name="document\_side" type="string" required=true %}
"FRONT" or "BACK"
{% endapi-method-parameter %}

{% api-method-parameter name="mime\_type" type="string" required=true %}
"IMAGE\_PNG" or "IMAGE\_JPG"
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{ 
  "account_id": "ISGA-4-0c0abb666a6a4fa38f0c21260ed99ce8",
  "document_side": "FRONT",
  "document_type":"RG",
  "status":"ANALYZING" 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Document details

To validate a Brazilian account, **3 documents must be sent**: 

1. "FRONT" -&gt; "SELFIE"
2. "FRONT" -&gt; Personal Document
3. "BACK" -&gt; Personal Document

Personal Document can be either RG \(Registro Geral or Carteira de Identidade\) or CNH \(Carteira Nacional de Habilitação\).

