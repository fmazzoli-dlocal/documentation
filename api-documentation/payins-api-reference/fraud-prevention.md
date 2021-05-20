# Fraud Prevention

## dLocal Defense

[dLocal Defense](https://dlocal.com/our-solution/fraud-prevention/), our fraud prevention solution, is an integral part of our service and is included for all merchant accounts. With dLocal Defense, all transactions processed by dLocal are run through our fraud prevention engine, which identifies market and industry-specific fraud patterns and prevents potentially fraudulent transactions from being processed.

In order to obtain the best results from dLocal Defense, it is **required** that as much information as possible is provided in the Payments API call \(as documented [here](payments/)\). 

{% hint style="info" %}
**Required payment information** used for fraud prevention includes the following:

* Payer's name and surname
* Email address
* Phone number
* Document
* Shipping address, otherwise billing address
* IP address
* User reference \(user ID\)
* Product details \(see Item object definition below\)
* Device ID \(see [below](fraud-prevention.md#device-id)\)

**For PSPs / Marketplaces:**

* Sub-merchant name
{% endhint %}

## Additional information for fraud prevention

For a more in-depth analysis of transactions for fraud patterns, we recommend that our merchants also consider using the `additional_risk_data` object in their Payment API calls. This object includes a list of optional properties which can be used to better identify fraudulent transactions. All objects and properties within the Additional Risk Data object and all its contained objects are considered **optional**, so merchants may provide the information that applies for their particular case.

#### The Additional Risk Data object

{% tabs %}
{% tab title="Additional Risk Data object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| `submerchant` | Submerchant object | Information on the submerchant account. **Required for PSPs / Marketplaces**. |
| `shipping` | Shipping object | Information on the shipping / alternative address. **Required for Retail**. |
| `beneficiary` | Beneficiary object | Information on the beneficiary, if different from the payer. Optional. |
| `basket` | List of Item objects | Information on the items purchased. **Required**. |
| `payer` | Payer object | Additional information on the payer's user account. Optional. |
| `device` | Device object | Additional information on the device used for purchase. Optional. |
{% endtab %}

{% tab title="Example Payment with Additional Risk Data object" %}
```javascript
{
    "amount": 399.80,
    "currency" : "USD",
    "country": "BR",
    "payment_method_id" : "CARD",
    "payment_method_flow" : "DIRECT",
    "payer":{
        "name" : "Thiago Gabriel",
        "email" : "thiago@example.com",
        "document" : "53033315550",
        "user_reference": "12345",
        "address": {
            "state"  : "Rio de Janeiro",
            "city" : "Volta Redonda",
            "zip_code" : "27275-595",
            "street" : "Servidao B-1",
            "number" : "1106"
        }
    },
    "card":{
        "holder_name" : "Thiago Gabriel",
        "number" : "4111111111111111",
        "cvv" : "123",
        "expiration_month" : 10,
        "expiration_year" : 2040
    },
    "order_id": "657434343",
    "notification_url": "http://merchant.com/notifications",
    "additional_risk_data": {
        "submerchant": {
            "merchant_reference" : "12534",
            "name" : "Submerchant name",
            "website" : "https://www.submerchant.com",
            "industry" : 17
        },
        "shipping" : {
            "address" : {
                "state" : "Montevideo",
                "city" : "Montevideo",
                "zip_code": "11300",
                "street" : "Avda. Brasil",
                "number": "1234 Ap. 501"
            },
            "is_physical" : true
        },
        "beneficiary" : {
            "email" : "beneficiary@example.org",
            "name" : "John Doe",
            "phone" : "09671268364",
            "document" : "513672561"
        },
        "basket" : [
            {
                "unit_price" : 199.90,
                "brand" : "Smoogle",
                "category" : "Smartphone",
                "item_reference" : "SP-562138",
                "upc": "1758929364928",
                "manufacturer" : "Smoogle",
                "product_name" : "Pexel 25",
                "quantity" : 2,
                "size" : "regular"
            }
        ],
        "payer" : {
            "email_is_valid" : true,
            "phone_is_valid" : false,
            "account_creation_date" : "20201110",
            "first_purchase_date" : "20201110",
            "is_positive" : false
        },
        "device" : {
            "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36",
            "geolocation" : "-34.8798853,-56.1867859",
            "locale": "en-US"
        }
    }
}
```
{% endtab %}
{% endtabs %}

#### The Submerchant object

For PSPs / merchants with sub-merchant accounts, the submerchant object may be used to provide more information on the specific sub-merchant for which the payment was issued.

{% tabs %}
{% tab title="Submerchant object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| `merchant_reference` | String | The ID / reference of the sub-merchant account. Optional. |
| `name` | String | Sub-merchant name. **Required for PSPs / marketplaces**. |
| `website` | String | Sub-merchant website. Optional. |
| `industry` | Number  | Sub-merchant industry, see [industry codes list](fraud-prevention.md#industry-codes). Optional. |
{% endtab %}

{% tab title="Example Submerchant object" %}
```javascript
"submerchant": {
    "merchant_reference" : "12534",
    "name" : "Submerchant name",
    "website" : "https://www.submerchant.com",
    "industry" : 17
}
```
{% endtab %}
{% endtabs %}

#### The Shipping object

For merchants who handle separate Payment / Shipping addresses, the Shipping object may be used to specify the shipping address, and also to indicate whether the purchase has a physical delivery or not \(i.e. retail vs digital goods\).

{% tabs %}
{% tab title="Shipping object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| `address` | Address object | Represents the address, documented in this table. Optional. |
| `address.state` | String | State. Optional. |
| `address.city` | String | City. Optional. |
| `address.zip_code` | String | Zip code. Optional. |
| `address.street` | String | Street. Optional. |
| `address.number` | String | Street number. Optional. |
| `is_physical` | Boolean | True if a physical delivery to this address is involved \(i.e. for retail goods\). Optional. |
{% endtab %}

{% tab title="Example Shipping object" %}
```javascript
"shipping" : {
    "address" : {
        "state" : "Montevideo",
        "city" : "Montevideo",
        "zip_code": "11300",
        "street" : "Avda. Brasil",
        "number": "1234 Ap. 501"
    },
    "is_physical" : true
}
```
{% endtab %}
{% endtabs %}

#### The Beneficiary object

For purchases where the beneficiary / recipient is not the payer \(e.g. for gifts of physical / virtual goods\), the Beneficiary object may be used to provide information on the product or service's recipient.

{% tabs %}
{% tab title="Beneficiary object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| `email` | String | Email address. Optional. |
| `name` | String | Name & surname. Optional. |
| `phone` | String | Phone number. Optional. |
| `document` | String | Document. Optional. |
{% endtab %}

{% tab title="Example Beneficiary object" %}
```javascript
"beneficiary" : {
    "email" : "beneficiary@example.org",
    "name" : "John Doe",
    "phone" : "09671268364",
    "document" : "513672561"
}
```
{% endtab %}
{% endtabs %}

#### The Item object

The `basket` property contains a **list of Item objects**, used to provide information on the items purchased. Item objects are required for effective fraud prevention, within these the properties marked with "Recommended" are the most recommended ones to include.

{% tabs %}
{% tab title="Item object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| `unit_price` | Number | Unit price. **Recommended**. |
| `brand` | String | Product brand. Optional. |
| `category` | String | Product category. **Recommended**. |
| `item_reference` | String | Item ID / Reference. **Recommended**. |
| `upc` | String | Universal Product Code. Optional. |
| `manufacturer` | String | Product manufacturer. Optional. |
| `product_name` | String | Product or service name. **Recommended**. |
| `quantity` | Number | Quantity of items purchased. **Recommended** |
| `size` | String | Product size \(e.g. S, M, L, XL\). Optional. |
{% endtab %}

{% tab title="Example Basket & Item object" %}
```javascript
"basket" : [
    {
        "unit_price" : 499.90,
        "brand" : "Google",
        "category" : "Smartphones",
        "item_reference" : "SP-562138",
        "upc": "1758929364928",
        "manufacturer" : "Google",
        "product_name" : "Pixel 3",
        "quantity" : 2,
        "size" : "XL"
    }
],
```
{% endtab %}
{% endtabs %}

#### The Payer object

The Payer object within the Additional Risk Data object allows for providing additional information on the payer's user account.

{% tabs %}
{% tab title="Payer object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| `email_is_valid` | Boolean | Set to True if the payer's email has been validated. Optional. |
| `phone_is_valid` | Boolean | Set to True if the payer's phone number has been validated. Optional. |
| `account_creation_date` | String | Date of account creation in `YYYYMMDD` format. Optional. |
| `first_purchase_date` | String | Date of first successful purchase in `YYYYMMDD` format. Optional. |
| `is_positive` | Boolean | Set to True if this payer is considered as a positive user by the merchant, e.g. for regular customers with a good purchase history. Optional. |
{% endtab %}

{% tab title="Example Payer object" %}
```javascript
"payer" : {
    "email_is_valid" : true,
    "phone_is_valid" : false,
    "account_creation_date" : "20201110",
    "first_purchase_date" : "20201110",
    "is_positive" : false
}
```
{% endtab %}
{% endtabs %}

#### The Device object

The Device object is used to store information on the device \(i.e. laptop, smartphone\) used to make the purchase.

{% tabs %}
{% tab title="Device object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| `user_agent` | String | Browser's User Agent property. Optional. |
| `geolocation` | String | User's geolocation. Optional. |
| `locale` | String | Browser's locale. Optional. |
{% endtab %}

{% tab title="Example Device object" %}
```javascript
"device" : {
    "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36",
    "geolocation" : "-34.8798853,-56.1867859",
    "locale": "en-US"
}
```
{% endtab %}
{% endtabs %}

## Device ID

In order to capture a Device ID from the user's device, we recommend that merchants use the following Javascript code in their website. The result returned by calling the `generateDeviceId()` function should be sent in the `device_id` parameter in the [Payment request](payments/#create-a-payment).

```javascript
export function generateDeviceId() {
    var nav = window.navigator;
    var screen = window.screen;
    var deviceId = nav.mimeTypes.length;
    Object.values(navigator.mimeTypes).forEach(p => deviceId += p.type);
    deviceId += nav.userAgent.replace(/\D+/g, '');//Only use digits
    deviceId += nav.plugins.length;
    Object.values(navigator.plugins).forEach(p => deviceId += p.filename);
    deviceId += screen.height || '';
    deviceId += screen.width || '';
    deviceId += screen.pixelDepth || '';
    return checksum(deviceId);
};
export function checksum(s) {
    var hash = 0, strlen = s.length, i, c;
    if ( strlen === 0 ) {
        return hash;
    }
    for ( i = 0; i < strlen; i++ ) {
        c = s.charCodeAt( i );
        hash = ((hash << 5) - hash) + c;
        hash = hash & hash; // Convert to 32bit integer
    }
    return Math.abs(hash);
};
```

## Appendix - Codes

### Industry codes list

| Code | Industry |
| :--- | :--- |
| 1 | Advertising |
| 2 | Antivirus |
| 3 | Delivery |
| 4 | Donations |
| 5 | Education |
| 6 | Gaming |
| 7 | Healthcare |
| 8 | Hosting |
| 9 | Investing / Financial services |
| 10 | IT Services |
| 11 | Marketplace |
| 12 | Money remittance |
| 13 | Payroll |
| 14 | Prepaid cards |
| 15 | PSP |
| 16 | Retail - Offline |
| 17 | Retail - Online |
| 18 | Ridesharing |
| 19 | SaaS |
| 20 | Social |
| 21 | Software / Apps |
| 22 | Streaming |
| 23 | Transport |
| 24 | Travel |
| 25 | Wallet |
| 26 | Dating |
| 999 | Others |



