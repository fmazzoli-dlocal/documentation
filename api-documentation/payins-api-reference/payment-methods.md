# Payment Methods

Object that identifies each payment method accepted by dLocal.

## The Payment Method Object

{% tabs %}
{% tab title="Payment Method Object" %}
| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | String | Payment method id |
| `type` | String | Type of method can be `CARD` `BANK_TRANSFER` `DIRECT_DEBIT` `TICKET`. |
| `name` | String | Payment type name |
| `countries` | String\[\] | Countries where the payment method is available. |
| `logo` | String | Payment method image url. |
| `allowed_flows` | String\[\] | Flows allowed for this payment, can be `DIRECT` or`REDIRECT`. |
{% endtab %}

{% tab title="Example Payment Method Object" %}
```yaml
{
  "id": "OX",
  "type": "TICKET",
  "name": "Oxxo",
  "countries" : ["MX"],
  "logo": "http://static.dlocal.com/payments-methods/OX/60x60",
  "allowed_flows": ["DIRECT", "REDIRECT"]
}
```
{% endtab %}
{% endtabs %}

{% api-method method="get" host=" https://api.dlocal.com/" path="payments-methods" %}
{% api-method-summary %}
Search Payment Methods
{% endapi-method-summary %}

{% api-method-description %}
This function returns a list of valid payment methods for the requested country.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="X-Date" type="string" required=true %}
ISO8601 Datetime with TimeZone.
{% endapi-method-parameter %}

{% api-method-parameter name="X-Login" type="string" required=true %}
Merchant xLogin
{% endapi-method-parameter %}

{% api-method-parameter name="X-Trans-Key" type="string" required=true %}
Merchant xTransKey
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
&lt;auth version&gt;, Signature: &lt;hmac\(secretKey, "X-Login+X-Date Header+RequestBody"\)&gt;
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="country" type="string" required=true %}
Payment method country code. See all country codes here.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
  {
      "id": "VI",
      "type": "CARD",
      "name": "Visa credit card",
      "logo": "http://static.dlocal.com/payments-methods/VI/60x60.png",
      "allowed_flows": ["DIRECT", "REDIRECT"]
  },
  {
      "id": "AE",
      "type": "CARD",
      "name": "American Express",
      "logo": "http://static.dlocal.com/payments-methods/AE/60x60.png",
      "allowed_flows": ["DIRECT", "REDIRECT"]
  },
  {
      "id": "GL",
      "type": "BANK_TRANSFER",
      "name": "Banco Galicia",
      "logo": "http://static.dlocal.com/payments-methods/BT/60x60.png",
      "allowed_flows": ["REDIRECT"]
  },
  {
      "id": "RP",
      "type": "TICKET",
      "name": "Rapi pago",
      "logo": "http://static.dlocal.com/payments-methods/RP/60x60.png",
      "allowed_flows": ["REDIRECT"]
  }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Example Request

```bash
curl -X GET \
    -H 'X-Date: 2018-02-20T15:44:42.310Z' \
    -H 'X-Login: sak223k2wdksdl2' \
    -H 'X-Trans-Key: fm12O7G9' \
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/payments-methods?country=AR
```



## Payment Method Codes

{% hint style="warning" %}
To make **credit/debit card** [**payments**](payments.md#create-a-payment), you should use`"CARD"` as the `payment_method_id`.  
For **other types of payments** \(eg: bank transfer\), you should use the corresponding payment\_method\_id found in the tables below.

Examples:   
- Payment with Visa credit card in Argentina, use `payment_method_id = "CARD"`  
- Payment with Rapi Pago in Argentina, use `payment_method_id = "RP"`
{% endhint %}

### **Argentina**

| **`payment_method_id`** | **Name** | **`payment_method_type`** | **Details** | **Logo** |
| :---: | :--- | :--- | :--- | :--- |
| `SI` | Santander Rio | `BANK_TRANSFER` | Bank Transfer Offline | https://pay.dlocal.com/views/2.0/images/payments/SI.png |
| `PF` | Pago Fácil | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/PF.png |
| `RP` | Rapi Pago | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/RP.png |
| `VI` | Visa | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| `MC` | MasterCard | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| `AE` | American Express | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| `DC` | Diners | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| `CM` | CMR Falabella | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/CM.png |
| `NJ` | Tarjeta Naranja | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/NJ.png |
| `TS` | Tarjeta Shopping | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/TS.png |
| `NT` | Nativa | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/NT.png |
| `CS` | Cencosud | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/CS.png |
| `CL` | Cabal | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/CL.png |
| `AG` | Argencard | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AG.png |
| `DB` | DirectDebit | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/DB.png |
| `VD` | Visa Debit | `CARD` | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/VD.png |
| `MD` | Mastercard Debit | `CARD` | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/MD.png |
| `MS` | Maestro Debit | `CARD` | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/MS.png |
| `CO` | Cordial | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/CO.png |
| `CB` | Cordobesa | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/CB.png |

### **Brazil**

| **`payment_method_id`** | **Name** | **`payment_method_type`** | **Details** | **Logo** |
| :---: | :--- | :--- | :--- | :--- |
| `BL` | Boleto | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/BL.png |
| `I` | Itau | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/I.png |
| `B` | Bradesco | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/B.png |
| `BB` | Banco do Brasil | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/BB.png |
| `CA` | Caixa | `BANK_TRANSFER` | Bank Transfer Offline | https://pay.dlocal.com/views/2.0/images/payments/CA.png |
| `SB` | Santander | `BANK_TRANSFER` | Bank Transfer Offline | https://pay.dlocal.com/views/2.0/images/payments/SB.png |
| `VI` | Visa | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| `MC` | MasterCard | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| `EL` | Elo | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/EL.png |
| `DC` | Diners Club | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| `HI` | Hipercard | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/HI.png |
| `ML` | Cartao MercadoLivre | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/ML.png |
| `AE` | American Express | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| `JC` | JCB | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/JC.png |
| `AU` | Aura | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AU.png |
| `DS` | Discover | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DS.png |

### **Chile**

| **`payment_method_id`** | **Description** | **`payment_method_type`** | **Details** | **Logo** |
| :---: | :--- | :--- | :--- | :--- |
| `WP` | WebPay | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| `VI` | Visa | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| `MC` | MasterCard | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| `DC` | Diners Club | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| `AE` | American Express | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| `PR` | Presto | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/PR.png |
| `CM` | CMR | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/CM.png |
| `MG` | Magna | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MG.png |
| `SP` | Servipag | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/SP.png |
| `WP` | BBVA | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| `WP` | Santander | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| `WP` | ITAU | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| `WP` | Corpbanca | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| `WP` | BCI-TBANC | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| `WP` | Banco Falabella | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| `WP` | Banco Estado | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| `WP` | Banco Bice | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| `WP` | Banco Security | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| `WP` | Banco Consorcio | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| `WP` | Banco Ripley | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| `WP` | ScotiaBank | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| `WP` | Coopeuch | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |

### **China**

| **`payment_method_id`** | **Name** | **`payment_method_type`** | Details | **Logo** |
| :---: | :--- | :--- | :--- | :--- |
| `EE` | ePayLinks | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/EE.png |
| `UP` | China Union Pay | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/UP.png |

### Colombia

| **`payment_method_id`** | **Name** | **`payment_method_type`** | **Details** | **Logo** |
| :---: | :--- | :--- | :--- | :--- |
| `EY` | Efecty | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/EY.png |
| `DA` | Davivienda | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/DA.png |
| `PC` | PSE | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `DB` | DirectDebit | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/DB.png |
| `EX` | Almacenes Éxito | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/EX.png |
| `BU` | Baloto | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/BU.png |
| `OC` | Banco de Occidente | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/OC.png |
| `CR` | Carulla | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/CR.png |
| `EQ` | Empresa de Energía del Quindio | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/EQ.png |
| `SX` | Surtimax | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/SX.png |
| `VI` | Visa | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| `MC` | MasterCard | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| `VD` | Visa Debit | `CARD` | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/VD.png |
| `MD` | MasterCard Debit | `CARD` | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/MD.png |
| `BN` | Boleto Bancolombia | `BANK_TRANSFER` | Bank Transfer Offline | https://pay.dlocal.com/views/2.0/images/payments/BN.png |
| `AE` | Amex | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| `DC` | Diners | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| `PC` | Banco Agrario | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Banco Av Villas | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Banco Caja Social | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Banco Colpatria | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Banco Corpbanca S.A. | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Banco de Bogota | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Banco de Occidente | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Banco GNB Sudameris | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Banco Pichincha S.A. | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Banco Popular | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Banco Procredit | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Bancolombia | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Bancoomeva S.A. | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | BBVA Colombia S.A. | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Citibank | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Helm Bank S.A. | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| `PC` | Banco Falabella | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |

### **India**

| **`payment_method_id`** | **Name** | **`payment_method_type`** | **Details** | **Logo** |
| :---: | :--- | :--- | :--- | :--- |
| `VI` | Visa | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| `MC` | MasterCard | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| `DC` | Diners Club | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| `AE` | American Express | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| `NB` | Netbanking | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/NB.png |
| `UI` | UPI | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/UI.png |
| `RU` | RuPay | `CARD` | Credit / Debit Card | https://pay.dlocal.com/views/2.0/images/payments/RU.png |

### **Mexico**

| **`payment_method_id`** | **Name** | **`payment_method_type`** | Details | **Logo** |
| :---: | :--- | :--- | :--- | :--- |
| `OX` | OXXO | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/OX.png |
| `SE` | SPEI | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/SE.png |
| `BV` | BBVA Bancomer | `TICKETTICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/BV.png |
| `BM` | Banamex | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/BM.png |
| `BN` | Banorte | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/BN.png |
| `SM` | Santander | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/SM.png |
| `VI` | Visa | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| `MC` | MasterCard | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| `VD` | Visa Debit | `CARD` | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/VD.png |
| `MD` | MasterCard Debit | `CARD` | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/MD.png |
| `AE` | American Express | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |

### **Morocco**

| **`payment_method_id`** | **Name** | **`payment_method_type`** | **Details** | **Logos** |
| :---: | :--- | :--- | :--- | :--- |
| `AM` | AmanPay | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/AM.png |
| `MI` | CMI | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MI.png |
| `VI` | Visa | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| `MC` | Mastercard | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |

### Paraguay

| **`payment_method_id`** | **Name** | **`payment_method_type`** | **Details** | **Logos** |
| :---: | :--- | :--- | :--- | :--- |
| `PE` | PagoExpress | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/PE.png |

### **Perú**

| **`payment_method_id`** | **Name** | **`payment_method_type`** | **Details** | **Logos** |
| :---: | :--- | :--- | :--- | :--- |
| `VI` | Visa | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| `MC` | Mastercard | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| `AE` | American Express | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| `DC` | Diners Club | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| `VD` | Visa Debit | `CARD` | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/VD.png |
| `EF` | Pago Efectivo | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/EF.png |
| `BC` | BCP | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/BC.png |
| `IB` | Interbank | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/IB.png |
| `BP` | BBVA | `BANK_TRANSFER` | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/BP.png |

### **Turkey**

| **`payment_method_id`** | **Name** | **`payment_method_type`** | **Details** | **Logos** |
| :---: | :--- | :--- | :--- | :--- |
| `AE` | Amex | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| `VI` | Visa | `CARD` | Credit / Debit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| `MC` | Mastercard | `CARD` | Credit / Debit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |

### **Uruguay**

| **`payment_method_id`** | **Name** | **`payment_method_type`** | **Details** | **Logos** |
| :---: | :--- | :--- | :--- | :--- |
| `VI` | Visa | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| `MC` | Mastercard | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| `DC` | Diners Club | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| `OA` | OCA | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/OA.png |
| `LI` | Lider | `CARD` | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/LI.png |
| `RE` | Red Pagos | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/RE.png |
| `AI` | Abitab | `TICKET` | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/AI.png |

