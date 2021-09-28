---
description: Learn how to handle the input of the card PIN field on your site.
---

# Set PIN

## Prerequisites to get started

### **HTTPS requirements**

All information using Smart Fields is made via a secure HTTPS connection. However, to protect yourself from certain forms of man-in-the-middle attacks, and to prevent your customers from seeing [Mixed Content](https://developers.google.com/web/fundamentals/security/prevent-mixed-content/what-is-mixed-content) warnings in modern browsers, you must serve the page containing the payment form over HTTPS as well.

## **PIN Setting**

### 1. Set up Smart Fields

Smart Fields is available as part of dLocal.js. To get started, include this script on your pages —it should always be loaded directly from [https://js.dlocal.com](https://js.dlocal.com).

For testing purposes, you can use [https://js-sandbox.dlocal.com](https://js-sandbox.dlocal.com)**.**

```markup
<script src="https://js.dlocal.com/"></script>
```

Next, create an instance of Smart Fields \(referred to as just `fields()`\):

```javascript
var dlocalInstance = dlocal('your_API_key');
var fields = dlocalInstance.fields({
    locale: 'es',
    country: 'CO'
});
```

{% hint style="warning" %}
To initialize the dLocal helper **you will need an API key**. Please contact your Technical Account Manager to obtain one. 
{% endhint %}

{% hint style="info" %}
For more information on dLocal.js, please visit our [dLocal.js Reference page](../dlocal.js-issuing-reference.md).
{% endhint %}

### 2. Create your form

To securely show card details from your customers, Smart Fields creates UI components for you that are hosted by dLocal. They are then placed into your form, rather than you creating them directly.

To determine where to insert these components, create empty DOM elements \(containers\) with unique IDs within your form.

For example:

```markup
<form>
    <div id="pin-field">
        <!-- A dLocal Smart Field will be inserted here. -->
    </div>
</form>
```

When the form above has loaded, create an instance of a Field and mount it to the Field container created above:

```javascript
// Custom styling can be passed to options when creating a Smart Field.
var style = {
    // Add your base input styles here. For example:
    base: {
        fontSize: '16px',
        fontFamily: "'Inter UI medium', sans-serif",
        lineHeight: '18px',
        fontSmoothing: 'antialiased',
        color: '#333',
        '::placeholder': {
            color: '#aab7c4'
        }
    }
};
// Create an instance of the PIN Field.
var pinField = fields.create('pin', { style, maskInput: true });
// Add an instance of the pin Field into the `pin-field` <div>.
pinField.mount(document.getElementById('pin-field'));
```

### **3. Tokenize the PIN**

Then you need to tokenize the PIN value obtained from the Smart Field through the `createPinToken` method.

```javascript
dlocalInstance.createPinToken(pinField)
    .then(function(result) {
        const pin_token = result.token; // result.token is the PIN tokenized
    })
```

### **4. Set PIN**

Once you have the PIN tokenized, you need to request a POST to `/cards/{card_id}/pin` with the following body payload:

```javascript
{
    "last_digits": "123456",
    "token": "pin_token"
}
```

#### Attribute Detail 

| Attribute | Description |
| :--- | :--- |
| `last_digitsT` | The last 6 digits of the card. |
| `token` | PIN tokenized \(successful response of [createPinToken method](../dlocal.js-issuing-reference.md#dlocal-createpintoken-field)\). |

