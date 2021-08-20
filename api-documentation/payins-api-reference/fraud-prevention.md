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
| `purchase` | Purchase object | The purchase object is used to provide additional general information about the purchase |
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
            "industry" : 17,
            "document" : "15236713521",
            "nationality" : "BR",
            "email" : "submerchant@gmail.com",
            "username" : "submerchant_username",
            "phone" : "123456712345",
            "created_date" : "20210311",
            "total_order_count" : 35,
            "total_order_amount" : 45020,
            "last_updated_date" : "20210312",
            "onboarding_ip_address" : "123.21.31.124",
            "onboarding_email" : "submerchant@gmail.com",
            "reputation" : 4,
            "ship_from_address" : {
                "state" : "Montevideo",
                "city" : "Montevideo",
                "zip_code": "11300",
                "street" : "Avda. Brasil",
                "number": "1234 Ap. 401"
            }
        },
        "shipping" : {
            "address" : {
                "state" : "Montevideo",
                "city" : "Montevideo",
                "zip_code": "11300",
                "street" : "Avda. Brasil",
                "number": "1234 Ap. 501"
            },
            "is_physical" : true,
            "cost" : 12.34,
            "delivery_company" : "FadEx",
            "method" : "FREE",
            "delivery_date" : "20211020",
            "is_forwarding_address" : false,
            "geolocation": "-34.8798853,-56.1867859"
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
                "size" : "regular",
                "subcategory": "Droid smartphones",
                "url": "https://www.merchant.com/products/SP-562138",
                "published_date": "20201113",
                "rating": 4.5,
                "count_reviews": 13,
                "image": "https://www.merchant.com/products/SP-562138/photos/1.jpg",
                "stock": 32,
                "weight": 0.34,
                "subscription": {
                    "id": "A15-D267125367",
                    "period": "P1M",
                    "current_period": 3,
                    "end_date": "20220101" 
                }
            }
        ],
        "payer" : {
            "email_is_valid" : true,
            "phone_is_valid" : false,
            "account_creation_date" : "20201110",
            "first_purchase_date" : "20201110",
            "is_positive" : false,
            "last_order_id": "1525634152634",
            "total_order_count": 12,
            "total_order_amount": 152.03,
            "last_updated_date": "20201020",
            "wish_list": [
                {
                    "item_reference": "125312435",
                    "unit_price": 1300,
                    "product_name": "Pexel 25 for dummies"
                }
            ],
            "reputation": 5
        },
        "purchase": {
            "is_retry": false,
            "channel": "WEB",
            "time_in_session": 55,
            "search_history": [
                {
                    "item_reference": "125312435",
                    "unit_price": 1300,
                    "product_name": "Pexel 25 for dummies"
                }
            ]
        },
        "discount_codes": [
            {
                "amount": 10,
                "percentage": 20,
                "code": "PROMO20OFF",
                "valid_until" : "20211130",
                "description" : "20% off Smoogle products"
            }
        ],
        "device" : {
            "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36",
            "geolocation" : "-34.8798853,-56.1867859",
            "locale": "en-US",
            "advertising_id" : "EA7583CD-A667-48BC-B806-42ECB2B48606",
            "vendor_id": "uapff_93e9a58cc03a0e7f45c2cf50ca567a99",
            "android_id": "cdda802e-fb9c-47ad-9866-0794d394c913",
            "media_drm_id": "0102030405060708090a0b0c0d0e0f10"
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
| `document` | String | Submerchant's document |
| `nationality` | String | Submerchant's nationality \(ISO 3166 country code\) |
| `email` | String | Submerchant's email address |
| `username` | String | The unique username associated with the seller's online account. |
| `phone` | String | Phone number |
| `created_date` | String | Date of account creation in YYYYMMDD format |
| `total_order_count` | Number | The total count of orders sold by this seller |
| `total_order_amount` | Number | The total amount sold by this seller \(in USD\) |
| `last_updated_date` | String | The last time a change was made to this submerchant \(e.g. changed address\).YYYYMMDD format. |
| `onboarding_ip_address` | String | The IP address of the device used when this seller account was created. |
| `onboarding_email` | String | The email used when this seller account was created. |
| `reputation` | Number | The reputation of the submerchant, from 0 \(negative\) to 5 \(positive\) |
| `ship_from_address` | Object | The address from where the submerchant ships the orders |
| `ship_from_address.street` | String | Street |
| `ship_from_address.number` | String | Street number |
| `ship_from_address.city` | String | City |
| `ship_from_address.zip_code` | String | Zip Code |
| `ship_from_address.state` | String | State |
{% endtab %}

{% tab title="Example Submerchant object" %}
```javascript
"submerchant": {
            "merchant_reference" : "12534",
            "name" : "Submerchant name",
            "website" : "https://www.submerchant.com",
            "industry" : 17,
            "document" : "15236713521",
            "nationality" : "BR",
            "email" : "submerchant@gmail.com",
            "username" : "submerchant_username",
            "phone" : "123456712345",
            "created_date" : "20210311",
            "total_order_count" : 35,
            "total_order_amount" : 45020,
            "last_updated_date" : "20210312",
            "onboarding_ip_address" : "123.21.31.124",
            "onboarding_email" : "submerchant@gmail.com",
            "reputation" : 4,
            "ship_from_address" : {
                "state" : "Montevideo",
                "city" : "Montevideo",
                "zip_code": "11300",
                "street" : "Avda. Brasil",
                "number": "1234 Ap. 401"
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
| `cost` | Number | Cost of the delivery \(in USD\) |
| `delivery_company` | String | Name of the delivery company |
| `method` | String | The type of shipment selected during checkout. [See list below](https://docs.dlocal.com/api-documentation/payins-api-reference/fraud-prevention#shipping-methods-list) |
| `delivery_date` | String | Shipping delivery date. in YYYYMMDD format. |
| `is_fowarding_address` | Boolean | If the shipping address is a forwarding address |
| `geolocation` | String | Shipping geolocation |
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
            "is_physical" : true,
            "cost" : 12.34,
            "delivery_company" : "FadEx",
            "method" : "FREE",
            "delivery_date" : "20211020",
            "is_forwarding_address" : false,
            "geolocation": "-34.8798853,-56.1867859"
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
| `subcategory` | String | The item subcategory |
| `url` | String | The item url |
| `published_date` | String | Date when the product was added / published in the store. In YYYYMMDD format |
| `rating` | Number | The product rating, as a score from 1 to 5 |
| `count_reviews` | Number | Number of customer reviews the product has received |
| `image` | String | The url with the product image |
| `stock` | Number | The quantity of products avaliable for sale |
| `weight` | Number | The product weight in kg |
| `subscription` | Object | A subscription object can be used to specify additional data for subscription business models |
| `subscription.id` | String | Subcription ID/reference |
| `subscription.period` | String | Renewal period in ISO 8601 format \(P1M, P3M, P1Y etc\) |
| `subscription.current_period` | Number | The current suscription period that the recurring order belongs |
| `subscription.end_date` | String | Suscription end date. YYYYMMDD format |
{% endtab %}

{% tab title="Example Basket & Item object" %}
```javascript
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
                "size" : "regular",
                "subcategory": "Droid smartphones",
                "url": "https://www.merchant.com/products/SP-562138",
                "published_date": "20201113",
                "rating": 4.5,
                "count_reviews": 13,
                "image": "https://www.merchant.com/products/SP-562138/photos/1.jpg",
                "stock": 32,
                "weight": 0.34,
                "subscription": {
                    "id": "A15-D267125367",
                    "period": "P1M",
                    "current_period": 3,
                    "end_date": "20220101" 
                }
            }
        ]
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
| `last_order_id` | String | Last order id placed by this account, not including the current order |
| `total_order_count` | Number | The total count of orders purchased by this account |
| `total_order_amount` | Number | The total amount purchased by this account |
| `last_updated_date` | String | The last time a change was made to this account \(e.g. changed address\).YYYYMMDD format. |
| `wish_list` | Array | A list of items that the user has in any or all of their favorites lists |
| `wish_list.item_reference` | String | Item ID |
| `wish_list.unit_price` | Number | Item unit price |
| `wish_list.product_name` | String | Item name |
| `reputation` | Number | The reputation of the payer, from 0 \(negative\) to 5 \(positive\) |
{% endtab %}

{% tab title="Example Payer object" %}
```javascript
"payer" : {
            "email_is_valid" : true,
            "phone_is_valid" : false,
            "account_creation_date" : "20201110",
            "first_purchase_date" : "20201110",
            "is_positive" : false,
            "last_order_id": "1525634152634",
            "total_order_count": 12,
            "total_order_amount": 152.03,
            "last_updated_date": "20201020",
            "wish_list": [
                {
                    "item_reference": "125312435",
                    "unit_price": 1300,
                    "product_name": "Pexel 25 for dummies"
                }
            ],
            "reputation": 5
        }
```
{% endtab %}
{% endtabs %}

#### The Discount codes list

The discount\_codes list is a list of entries that represent the discount codes or promotions that are applied to this purchase

{% tabs %}
{% tab title="Discount code object" %}
| `Property` | Type | Description |
| :--- | :--- | :--- |
|  |  |  |
| `amount` | Number | Product discount amount at the moment of the purchase. |
| `percentage` | Number | If a percentage discount is applied the percentage of the total order amount the discount applies to. e.g. 20% off purchase. This field should be NULL if amount is provided. |
| `code` | String | The id of the discount / code used. |
| `valid_until` | String | Promotion end date. In YYYYMMDD format |
| `description` | String | A description of the discount |
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
| `advertising_id` | String | An advertising ID is a unique user ID assigned to a mobile device, or operating environment\(apple: advertisingIdentifier, android: GSF Id\) |
| `vendor_id` | String | For Apple, an alphanumeric string that uniquely identifies a device to the vendor \(identifierForVendor\) |
| `android_id` | String | For Android, 64-bit number \(as a hex String\) that the OS randomly generates when the user first sets up the device |
| `media_drm_id` | String | For Android, the MediaDrm device unique ID |
{% endtab %}

{% tab title="Example Device object" %}
```javascript
"device" : {
            "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36",
            "geolocation" : "-34.8798853,-56.1867859",
            "locale": "en-US",
            "advertising_id" : "EA7583CD-A667-48BC-B806-42ECB2B48606",
            "vendor_id": "uapff_93e9a58cc03a0e7f45c2cf50ca567a99",
            "android_id": "cdda802e-fb9c-47ad-9866-0794d394c913",
            "media_drm_id": "0102030405060708090a0b0c0d0e0f10"
        }
```
{% endtab %}
{% endtabs %}

#### The Purchase object

The purchase object is used to provide additional general information about the purchase

{% tabs %}
{% tab title="Purchase object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| `is_retry` | Boolean | Indicates if the payment is a retry by the user of the same previously rejected purchase attempt. |
| `channel` | String | The channel or source where the order was placed, see list. [See list below](https://docs.dlocal.com/api-documentation/payins-api-reference/fraud-prevention#purchase-channel-list) |
| `time_in_session` | String | The time in seconds that a user spent within the session in the website or app before making the purchase. |
| `search_history` | Array | The search\_history list contains the list of products that the user visited within the session before making the purchase. |
| `search_history.item_reference` | String | The item ID |
| `search_history.unit_price` | String | The item's unit price |
| `search_history.product_name` | String | The item's product name |
{% endtab %}

{% tab title="Example Purchase object" %}


```javascript
        "purchase": {
            "is_retry": false,
            "channel": "WEB",
            "time_in_session": 55,
            "search_history": [
                {
                    "item_reference": "125312435",
                    "unit_price": 1300,
                    "product_name": "Pexel 25 for dummies"
                }
            ]
        }
```
{% endtab %}
{% endtabs %}

#### 

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

### Shipping methods list

| Code | Description |
| :--- | :--- |
| FREE | Free Shipping |
| PICKUP | Pickup in store |
| INTERNATIONAL | International |
| EXPRESS | Express |
| STANDARD | Standard |

### Purchase channel list

| Code | Description |
| :--- | :--- |
| WEB | Users buy through the website |
| PHONE | Orders made by phone calls |
| MOBILE\_APP | Users buy through a mobile application |
| SOCIAL | Users buy through a social network platform \(facebook, instagram\) |
| MARKETPLACE | Users buy in an ecommerce store where products are sold by multiple sellers \(Amazon\) |
| IN\_STORE | Orders purchased in a physical store |

