# Retrieve card

dLocal provides a JavaScript library that enables you to display sensitive card data in your application or webpage while limiting your data security compliance burden.

Our solution accomplishes this by rendering an iframe to show the **Card Number, CVV** and **Expiration date** fields on  your web page while ensuring that you are compliant with PCI requirements.

## **Before you start: HTTPS requirements**

All info using Smart Fields are made via a secure HTTPS connection. However, to protect yourself from certain forms of man-in-the-middle attacks, and to prevent your customers from seeing [Mixed Content](https://developers.google.com/web/fundamentals/security/prevent-mixed-content/what-is-mixed-content) warnings in modern browsers, you must serve the page containing the payment form over HTTPS as well.

## **Step 1: Request the card tokens** 

Each time you want to display a virtual card’s sensitive data, you must request a new client access token. The client access token expires after ten minutes and it's valid for 1 time.

Uses the [Get Card Information ](get-card-information.md)service to generate the card's tokens \(`card_information`\)  using the `full_data` parameter in `true`.

## Step 2: Set up Smart Fields

Smart Fields is available as part of dLocal.js. To get started, include this script on your pages—it should always be loaded directly from [https://js.dlocal.com](https://js.dlocal.com). For testing purposes, you can use [https://js-sandbox.dlocal.com](https://js-sandbox.dlocal.com)**.**

```markup
<script src="https://js.dlocal.com/"></script>
```

Next, create an instance of Smart Fields \(referred to as just `fields()`\):

```javascript
var dlocal = dlocal('your_API_key');
var fields = dlocal.fields({
   locale:'en',
   country:'BR',
   cardToken:{
      frontToken:'AQICAHjajCjj_m_SHvhC9QhV2CT_N062EgS6-BUD2Ddfq2y_iAGoLHvoSHaQCwGSJOeFpyYwA',
      rearToken:'AAAhjCBgwYJKoZIhvcNAQcGoHYwdAIBADBvBgkqhkiG9w0BBwEwHgYJYIZIAWUDBAEuMBEEDI1qTNda'
   }
});
```

{% hint style="info" %}
To initialize the dlocal helper you will need an **API Key**. Please contact your Technical Account Manager to obtain one. 

For more information on dLocal.js, please visit our [_**dLocal.js Reference page**_](../../../products/smart-fields/dlocal.js-reference.md).
{% endhint %}

## Step 3: Create your form

To securely show card details from your customers, Smart Fields creates UI components for you that are hosted by dLocal. They are then placed into your form, rather than you creating them directly**.**  
To determine where to insert these components, create empty DOM elements \(containers\) with unique IDs within your payment form.

For example:

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



