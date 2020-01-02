# Submit a payout

{% api-method method="post" host="https://api.dlocal.com/api\_curl/cashout\_api" path="/request\_cashout" %}
{% api-method-summary %}
Requesting a payout
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="login" type="string" required=true %}
Your merchant ID in dLocal platform  
-Length: 32 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="pass" type="string" required=true %}
Your merchant password in dLocal platform  
-Length: 32 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="external\_id" type="string" required=true %}
Payout identification \(at the merchant site\)  
-Max. 100 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="document\_id" type="string" required=false %}
Beneficiary's personal identification number  
-Max. 100 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="document\_type" type="string" required=false %}
Beneficiary's personal identification type  
-Max. 10 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="beneficiary\_name" type="string" required=true %}
Beneficiary's name or company  
-Max. 100 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="beneficiary\_lastname" type="string" required=false %}
Beneficiary's surname  
-Max. 100 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="country" type="string" required=true %}
The user's country. **ISO 3166-1 alpha-2 code**  
-Length: 2 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="bank\_code" type="integer" required=false %}
Beneficiary's bank code. See Bank codes
{% endapi-method-parameter %}

{% api-method-parameter name="bank\_name" type="string" required=false %}
Beneficiary's bank name. See bank names  
-Max. 40 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="bank\_province" type="string" required=false %}
Beneficiary's bank province name  
-Max. 40 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="bank\_city" type="string" required=false %}
Beneficiary's bank city name  
-Max. 40 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="bank\_branch\_name" type="string" required=false %}
Beneficiary's bank branch name  
-Max. 40 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="bank\_branch" type="string" required=false %}
Beneficiary's bank branch number  
-Max. 45 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="bank\_account" type="string" required=true %}
Beneficiary's bank account number  
-Max. 45 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="account\_type" type="string" required=false %}
The type of the account.  
**C** for checking accounts, **S** for savings accounts, **M** for Maestra accounts \(only Peru\)  
-Length: 1 chars-  
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="number" required=true %}
Payout amount \(in the currency entered in the field 'currency'\)  
-Max. 2 decimal numbers-
{% endapi-method-parameter %}

{% api-method-parameter name="control" type="string" required=false %}
Control string
{% endapi-method-parameter %}

{% api-method-parameter name="address" type="string" required=false %}
Address of the beneficiary  
-Max. 200 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="birthday" type="string" required=false %}
Beneficiary's birth date  
-Format: 'YYYYMMDD'-
{% endapi-method-parameter %}

{% api-method-parameter name="city" type="string" required=false %}
City of the beneficiary  
-Max. 100 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="comments" type="string" required=false %}
A commentary for this payout  
-Max. 200 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="currency" type="string" required=false %}
Each country accepts USD and local currency.  
**Default: USD**  
-Length: 3 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=false %}
Email of the beneficiary  
-Max. 100 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="phone" type="string" required=false %}
Phone number of the beneficiary  
-Max. 20 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="extra\_info" type="string" required=false %}
Extra info of the beneficiary in json format  
-Max. 500 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="notification\_url" type="string" required=false %}
To be provided if the notification URL is different from the notification URL defined by default  
-Max. 100 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="on\_hold" type="boolean" required=false %}
If the merchant wants to hold the payout and set it to process later through the merchants panel  
**Default: 0**  
-Boolean 1 or 0-
{% endapi-method-parameter %}

{% api-method-parameter name="postal\_code" type="string" required=false %}
Postal code of the beneficiary  
-Max. 20 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=false %}
Response type xml or json.  
**Default: json**
{% endapi-method-parameter %}

{% api-method-parameter name="remitter\_address" type="string" required=false %}
Remitter's address  
-Max. 200 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="remitter\_bank\_account" type="string" required=false %}
Remitter's bank account  
-Max. 45 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="remitter\_full\_name" type="string" required=false %}
Remitter's full name  
-Max. 200 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="remitter\_document" type="string" required=false %}
Remitter's document  
-Max. 45 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="remitter\_city" type="string" required=false %}
Remitter's bank city name  
-Max. 40 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="remitter\_country" type="string" required=false %}
The remitter's country. **ISO 3166-1 alpha-2 code**  
-Max. 2 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="remitter\_postal\_code" type="string" required=false %}
Postal code of the remitter  
-Max. 20 chars-
{% endapi-method-parameter %}

{% api-method-parameter name="remitter\_birth\_date" type="string" required=false %}
Remitter's birthdate  
-Format: 'YYYYMMDD'-
{% endapi-method-parameter %}

{% api-method-parameter name="purpose" type="string" required=true %}
Payout purpose code. See purpose codes.  
-Length: 6 chars-
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Request OK
{% endapi-method-response-example-description %}

```java
{
“status”:0,
“cashout_id”:123456,
“desc”:“OK”
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The external ID exceeds the validate length
{% endapi-method-response-example-description %}

```
{
“status”: 1,
“desc”: “Invalid param external_id”,
“error_code”: “300”
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="warning" %}
#### Depending on each country's bank compliance requirements, some additional fields might be mandatory when sending payouts. 
{% endhint %}

### See each country's requirements below:

* \*\*\*\*[**Argentina**](argentina.md)\*\*\*\*
  * [Example request for Argentina](argentina.md#example-request) 
* \*\*\*\*[**Brazil**](brazil.md)\*\*\*\*
  * [Example request for Brazil ](brazil.md#example-request)
* \*\*\*\*[**Chile**](chile.md)\*\*\*\*
  * [Example request for Chile](chile.md#example-request)
* \*\*\*\*[**China**](china.md)\*\*\*\*
  * [Example request for China](china.md#example-request)
* \*\*\*\*[**Colombia**](colombia.md)\*\*\*\*
  * [Example request for Colombia](colombia.md#example-request)
* \*\*\*\*[**Costa Rica**](costa-rica.md#mandatory-parameters)\*\*\*\*
  * [Example request for Costa Rica](costa-rica.md#example-request)
* \*\*\*\*[**Ecuador**](ecuador.md)\*\*\*\*
  * [Example request for Ecuador](ecuador.md#example-request) 
* \*\*\*\*[**India**](india.md)\*\*\*\*
  * [Example request for India ](india.md#example-request)
* \*\*\*\*[**Mexico**](mexico.md)\*\*\*\*
  * [Example request for Mexico](mexico.md#example-request)
* \*\*\*\*[**Peru**](peru.md)\*\*\*\*
  * [Example request for Peru](peru.md#example-request)
* \*\*\*\*[**Uruguay**](uruguay.md)\*\*\*\*
  * [Example request for Uruguay](uruguay.md#example-request)
* \*\*\*\*[**Egypt**](egypt.md)\*\*\*\*
  * [Example request for Egypt](egypt.md#example-request)

{% hint style="info" %}
**x\_login** and **x\_trans\_key** are your credentials.                                                                            

Remember to find them in the panel, section Integration -&gt; Credentials & Settings.
{% endhint %}



