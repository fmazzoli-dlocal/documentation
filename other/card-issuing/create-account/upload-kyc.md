# Upload KYC

This function is to send KYC files in order to provide necessary documentation to validate the account. Only used for **Brazil**.

https://sandbox.dlocal.com/issuing/accounts/{account\_id}/images

Path Parameters

Account id provided when account owner was created

Form Data Parameters

"SELFIE", "RG" or "CNH". Max 1MB

"IMAGE\_PNG" or "IMAGE\_JPG"

```text
{   "account_id": "ISGA-4-0c0abb666a6a4fa38f0c21260ed99ce8",  "document_side": "FRONT",  "document_type":"RG",  "status":"ANALYZING" }
```

For **Brazil**, 3 documents must be sent:

* "FRONT" -&gt; "SELFIE"
* "FRONT" -&gt; Personal Document
* "BACK" -&gt; Personal Document

Personal Document can be either RG \(Registro Geral or Carteira de Identidade\) or CNH \(Carteira Nacional de Habilitação\)

