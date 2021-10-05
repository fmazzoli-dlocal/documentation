---
description: Learn how to create a payment form using dLocal's all-in-one card Smart Field.
---

# Retrieve card data

dLocal provides a JavaScript library that enables you to **display sensitive card data in your application or webpage while limiting your data security compliance burden**.

Our solution accomplishes this by rendering an iframe to show the **Card Number, CVV** and **Expiration date** fields on your web page while ensuring that you are compliant with PCI requirements.

## Prerequisites to get started

### **HTTPS requirements**

All info using Smart Fields are made via a secure HTTPS connection. However, to protect yourself from certain forms of man-in-the-middle attacks, and to prevent your customers from seeing [Mixed Content](https://developers.google.com/web/fundamentals/security/prevent-mixed-content/what-is-mixed-content) warnings in modern browsers, you must serve the page containing the payment form over HTTPS as well.

## **Card data capture**

### **1. Request the card tokens** 

Each time you want to display a virtual card’s sensitive data, you must request a new client access token. The client access token expires after ten minutes and it's valid for 1 time.

Uses the [Get Card Information ](get-card-information.md)service to generate the card's tokens \(`card_information`\)  using the `full_data` parameter in `true`.

### 2. Set up Smart Fields

Smart Fields is available as part of dLocal.js. To get started, include this script on your pages—it should always be loaded directly from [https://js.dlocal.com](https://js.dlocal.com).

For testing purposes, you can use [https://js-sandbox.dlocal.com](https://js-sandbox.dlocal.com)**.**

```markup
<script src="https://js.dlocal.com/"></script>
```

Next, create an instance of Smart Fields \(referred to as just `fields()`\) according to the token supported by the country.

#### Colombia

 If you receive the `card_information_image` object use the following code: 

```javascript
var dlocalInstance = dlocal('your_API_key');
var fields = dlocalInstance.fields({
   locale:'es',
   country:'CO',
   cardInformationImage:{
      frontToken:'the card front token',
      rearToken:'the card rear token'
   }
});
```

#### Brazil and Mexico 

If you receive the `card_information_data` object use the following code:

```javascript
var dlocalInstance = dlocal('your_API_key');
var fields = dlocalInstance.fields({
    locale: 'es',
    country: 'MX',
    cardInformationData: {
	    panToken: 'The card PAN token',
	    expToken: 'The card expiration date token',
	    cvvToken: 'The card CVV2 token'
    }
});
```

{% hint style="warning" %}
To initialize the dLocal helper **you will need an API key**. Please contact your Technical Account Manager to obtain one. 
{% endhint %}

{% hint style="info" %}
For more information on dLocal.js, please visit our [dLocal.js Reference page](../../../products/smart-fields/dlocal.js-reference.md).
{% endhint %}

### 3. Create your form

To securely show card details from your customers, Smart Fields creates UI components for you that are hosted by dLocal. They are then placed into your form, rather than you creating them directly**.**  
To determine where to insert these components, create empty DOM elements \(containers\) with unique IDs within your form.

#### Colombia

 If you receive the `card_information_image` object use the following code: 

```markup
<form>
  <div id="virtual-card-field">
    <!-- A dLocal Smart Field will be inserted here. -->
  </div>
  <!-- Used to display Smart Field errors. -->
  <div id="virtual-card-errors" role="alert"></div>
</form>
```

When the form above has loaded, create an instance of a Field and mount it to the Field container created above:

```javascript
// Custom styling can be passed to options when creating a Smart Field.
var style = {
  base: {
    // Add your base input styles here. For example:
    lineHeight: '200px'
  }
};
// Create an instance of the card Field.
var card = fields.create('read-only-card', { style });
// Add an instance of the card Field into the `virtual-card-field` <div>.
card.mount(document.getElementById('virtual-card-field'));
```

#### Brazil and Mexico 

If you receive the `card_information_data` object use the following code:

```javascript
<form>
    <div id="pan-field">
        <!-- A dLocal Smart Field will be inserted here. -->
    </div>
    <div id="cvv-field">
        <!-- A dLocal Smart Field will be inserted here. -->
    </div>
    <div id="exp-field">
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
// Create an instance of the PAN Field.
var panField = fields.create('read-only-pan', { style });
// Add an instance of the pan Field into the `pan-field` <div>.
panField.mount(document.getElementById('pan-field'));

// Create an instance of the CVV Field.
var cvvField = fields.create('read-only-cvv', { style });
// Add an instance of the CVV Field into the `cvv-field` <div>.
cvvField.mount(document.getElementById('cvv-field'));

// Create an instance of the exp Field.
var expField = fields.create('read-only-expiration', { style });
// Add an instance of the exp Field into the `exp-field` <div>.
expField.mount(document.getElementById('exp-field'));
```

