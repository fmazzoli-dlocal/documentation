---
description: This service is only available for Nigeria
---

# Validation account endpoint - Nigeria

**Sandbox environment:**[**https://sandbox.dlocal.com/payouts/validations**  
](https://sandbox.dlocal.com/payouts/validations)**Production environment:** [**https://api.dlocal.com/payouts/validations**](https://api.dlocal.com/payouts/validations)



| **Header** | **Type** | **Description** |
| :--- | :--- | :--- |
| **x-Date** | **String** | **ISO8601 Datetime with Timezone. Eg 2020-07-12T13:46:28.629Z** |
| **x-Login** | **String** | **Merchant xLogin** |
| **x-Trans-Key** | **String** | **Merchant xTransKey** |
| **Content-Type** | **String** | **application/json** |
| **x-Version** | **String** | **Api Version** |
| **User-Agent** | **String** | **API Used to identify the application type, operating system, software vendor or software version of the requesting software user agent.** |
| **Authorization** | **String** | **&lt;auth version&gt;, Signature: &lt;hmac\(secretKey, "X-Login+X-Date Header+RequestBody"\)&gt;** |

**Generic request body**

```text
{
    "fields": {},
    "filters": {}
}

```

**Generic response body**

```text
{
  "code": "string",
  "message": "string",
  "result": {
    "data": [
      {}
    ]
  },
  "status": "string",
  "time_stamp": "2020-09-25T21:56:57.989Z"
}
```

  
**Example**

**Request for bank account validation in Nigeria:**

```text
{
   "fields":{
      "bank_account":"12345789",
      "bank_code" : "44"
   },
   "filters":{
      "country_code":"NG"
   }
}
```

**Response**

```text
{
  "status": "success",
  "code": "1000",
  "message": "Successful validation",
  "time_stamp": "2020-08-31T02:35:50.399",
  "result": {
    "data": [
      {
        "status": "success",
        "field_name": "bank_account",
        "message": "bank_account is valid.",
        "extra_info": [{"account_name": "Flutterwave Developer Account"}]
      }
    ]
  }
}

```

  
**Error codes:**

| Code | Message |
| :--- | :--- |
| 999 | Your request is badly formed, it was not possible to process |
| 1000 | Successful validation |
| 1001 | Failed validation |
| 1003 | Validation with partial errors |
| 1004 | You must add at least one validation field |
| 1005 | You must add at least one filter with valid fields. |
| 1006 | The entered filter is not supported. The allowed filters are %s |
| 1007 | An error occurred while trying to get the validation settings. |
| 1008 | No validation detail was found for the requested field. |
| 1009 | There is no validator for the combination of filters entered. |
| 1010 | No validation detail type was found for the requested field. |
| 500 | Invalid signature |

