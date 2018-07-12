# Payment Methods

Object that identifies each payment method accepted by dLocal.

## The Payment Method Object

{% tabs %}
{% tab title="Payment Method Object" %}
| **Property** | **Type** | **Description** |
| --- | --- | --- | --- | --- | --- | --- |
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
    -H 'Authorization: V2-HMAC-SHA256, Signature: 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
    https://api.dlocal.com/payments-methods?country=AR
```



## Payment Method Codes

### **Argentina**

| **Code** | **Description** | **Payment Type** | **Logo** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SI | Santander Rio | Bank Transfer Offline | https://pay.dlocal.com/views/2.0/images/payments/SI.png |
| PF | Pago Fácil | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/PF.png |
| RP | Rapi Pago | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/RP.png |
| VI | Visa | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| MC | MasterCard | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| AE | American Express | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| DC | Diners | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| CM | CMR Falabella | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/CM.png |
| NJ | Tarjeta Naranja | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/NJ.png |
| TS | Tarjeta Shopping | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/TS.png |
| NT | Nativa | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/NT.png |
| CS | Cencosud | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/CS.png |
| CL | Cabal | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/CL.png |
| AG | Argencard | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AG.png |
| VD | Visa Debit | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/VD.png |
| MD | Mastercard Debit | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/MD.png |
| MS | Maestro Debit | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/MS.png |
| CO | Cordial | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/CO.png |
| CB | Cordobesa | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/CB.png |

### **Brazil**

| **Code** | **Description** | **Payment Type** | **Logo** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| BL | Boleto | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/BL.png |
| I | Itau | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/I.png |
| B | Bradesco | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/B.png |
| BB | Banco do Brasil | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/BB.png |
| CA | Caixa | Bank Transfer Offline | https://pay.dlocal.com/views/2.0/images/payments/CA.png |
| SB | Santander | Bank Transfer Offline | https://pay.dlocal.com/views/2.0/images/payments/SB.png |
| VI | Visa | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| MC | MasterCard | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| EL | Elo | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/EL.png |
| DC | Diners Club | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| HI | Hipercard | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/HI.png |
| ML | Cartao MercadoLivre | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/ML.png |
| AE | American Express | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| JC | JCB | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/JC.png |
| AU | Aura | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AU.png |
| DS | Discover | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DS.png |

### **Chile**

| **Code** | **Description** | **Payment Type** | **Logo** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| WP | WebPay | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| VI | Visa | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| MC | MasterCard | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| DC | Diners Club | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| AE | American Express | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| PR | Presto | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/PR.png |
| CM | CMR | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/CM.png |
| MG | Magna | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MG.png |
| SP | Servipag | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/SP.png |
| WP | BBVA | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| WP | Santander | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| WP | ITAU | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| WP | Corpbanca | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| WP | BCI-TBANC | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| WP | Banco Falabella | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| WP | Banco Estado | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| WP | Banco Bice | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| WP | Banco Security | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| WP | Banco Consorcio | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| WP | Banco Ripley | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| WP | ScotiaBank | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |
| WP | Coopeuch | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/WP.png |

### **China**

| **Code** | **Description** | **Payment Type** | **Logo** |
| --- | --- | --- |
| EE | ePayLinks | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/EE.png |
| UP | China Union Pay | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/UP.png |

### Colombia

| **Code** | **Description** | **Payment Type** | **Logo** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| EY | Efecty | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/EY.png |
| DA | Davivienda | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/DA.png |
| PC | PSE | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| EX | Almacenes Éxito | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/EX.png |
| BU | Baloto | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/BU.png |
| OC | Banco de Occidente | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/OC.png |
| CR | Carulla | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/CR.png |
| EQ | Empresa de Energía del Quindio | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/EQ.png |
| SX | Surtimax | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/SX.png |
| VI | Visa | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| MC | MasterCard | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| VD | Visa Debit | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/VD.png |
| MD | MasterCard Debit | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/MD.png |
| BN | Boleto Bancolombia | Bank Transfer Offline | https://pay.dlocal.com/views/2.0/images/payments/BN.png |
| AE | Amex | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| DC | Diners | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| PC | Banco Agrario | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Banco Av Villas | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Banco Caja Social | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Banco Colpatria | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Banco Corpbanca S.A. | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Banco de Bogota | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Banco de Occidente | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Banco GNB Sudameris | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Banco Pichincha S.A. | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Banco Popular | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Banco Procredit | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Bancolombia | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Bancoomeva S.A. | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | BBVA Colombia S.A. | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Citibank | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Helm Bank S.A. | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |
| PC | Banco Falabella | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/PC.png |

### **India**

| **Code** | **Description** | **Payment Type** | **Logo** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| VI | Visa | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| MC | MasterCard | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| DC | Diners Club | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| AE | American Express | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| NB | Netbanking | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/NB.png |
| UI | UPI | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/UI.png |
| RU | RuPay | Credit / Debit Card | https://pay.dlocal.com/views/2.0/images/payments/RU.png |

### **Mexico**

| **Code** | **Description** | **Payment Type** | **Logo** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| OX | OXXO | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/OX.png |
| SE | SPEI | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/SE.png |
| BV | BBVA Bancomer | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/BV.png |
| BM | Banamex | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/BM.png |
| BN | Banorte | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/BN.png |
| SM | Santander | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/SM.png |
| VI | Visa | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| MC | MasterCard | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| VD | Visa Debit | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/VD.png |
| MD | MasterCard Debit | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/MD.png |
| AE | American Express | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |

### **Morocco**

| **Code** | **Description** | **Payment Type** | **Logos** |
| --- | --- | --- | --- | --- |
| AM | AmanPay | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/AM.png |
| MI | CMI | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MI.png |
| VI | Visa | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| MC | Mastercard | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |

### **Perú**

| **Code** | **Description** | **Payment Type** | **Logos** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| VI | Visa | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| MC | Mastercard | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| AE | American Express | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| DC | Diners Club | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| VD | Visa Debit | Debit Card | https://pay.dlocal.com/views/2.0/images/payments/VD.png |
| EF | Pago Efectivo | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/EF.png |
| BC | BCP | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/BC.png |
| IB | Interbank | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/IB.png |
| BP | BBVA | Bank Transfer Online | https://pay.dlocal.com/views/2.0/images/payments/BP.png |

### **Turkey**

| **Code** | **Description** | **Payment Type** | **Logos** |
| --- | --- | --- | --- |
| AE | Amex | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/AE.png |
| VI | Visa | Credit / Debit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| MC | Mastercard | Credit / Debit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |

### **Uruguay**

| **Code** | **Description** | **Payment Type** | **Logos** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| VI | Visa | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/VI.png |
| MC | Mastercard | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/MC.png |
| DC | Diners Club | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/DC.png |
| OA | OCA | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/OA.png |
| LI | Lider | Credit Card | https://pay.dlocal.com/views/2.0/images/payments/LI.png |
| RE | Red Pagos | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/RE.png |
| AI | Abitab | Cash Payment | https://pay.dlocal.com/views/2.0/images/payments/AI.png |

