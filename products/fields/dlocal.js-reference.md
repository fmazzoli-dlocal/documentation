---
description: >-
  This is the API reference for dlocal.js. Use dlocal.js’ APIs to tokenize
  sensitive card data using customizable dLocal Fields.
---

# dlocal.js Reference

### Including dlocal.js

However you’re using dlocal.js, you always begin by including the library and setting your API key. To get started, include this script on your pages—it should always be loaded directly from **https://js.dlocal.com**:

```text
<script src="https://js.dlocal.com/"></script>
```

## The dLocal Object

### `dlocal.fields([`_`options`_`])` 

Create pre-built UI components to collect payment information with [Fields](./).

```javascript
var fields = dlocal.fields();
```

This method creates an instance of `fields`, which manages a group of Fields. It accepts an optional`options` object. Available options are documented below:

| **Option** | **Type** | **Description** |
| --- | --- | --- |
| `fonts` | Array \(Optional\) | An array of custom fonts, which Elements created from the `elements` object can use.  Fonts can either be loaded via a CSS file by passing an object with the [cssSrc attribute](dlocal.js-reference.md#the-csssrc-attribute), **or** they can be loaded directly by passing a [Font object](dlocal.js-reference.md#the-font-object). |
| `locale` | String | The [IETF language tag](https://en.wikipedia.org/wiki/IETF_language_tag) of the locale to display placeholders and error strings in. Default is Spanish`(es)`. Supported values are: **es, en, pt, zh, cv, tr.** |

#### The cssSrc attribute

| **Parameter** | **Type** | **Description** |
| --- | --- |
| `cssSrc` | String | A relative or absolute URL pointing to a CSS file with [@font-face](https://developer.mozilla.org/en/docs/Web/CSS/@font-face) definitions, for example:  `"https://fonts.googleapis.com/css?family=Open+Sans"`  |

#### The Font object

| Parameter | Type | Description |
| --- | --- | --- | --- | --- | --- | --- |
| `family` | String | The name to give the font. |
| `src` | String | A valid [src ](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/src)value pointing to your custom font file. This is usually \(though not always\) a link to a file with a `.woff`, `.otf`, or `.svg` suffix. |
| `display` | String \(Optional\) | A valid [font-display ](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display)value. |
| `style` | String | One of `'normal'`, `'italic'`, `'oblique'`. Defaults to `'normal'`. |
| `unicodeRange` | String \(Optional\) | A valid [unicode-range ](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/unicode-range)value. |
| `weight` | String \(Optional\) | A valid [font-weight ](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight). Note that this is a string, not a number. |

### `dlocal.createToken(field, tokenData)` 

Use `dlocal.createToken()` to convert information collected by Fields into a  token that you safely pass to your server to use in an API call. **This token expires 10 minutes after it has been created**, so you need to make sure that the payment is made within that timeframe.

```javascript
dlocal.createToken(card,tokenData).then(function(result) {
  // Handle result.error or result.token
});
```

This method takes two arguments.

* `field`, the Field you wish to tokenize data from. If applicable, the Field pulls data from other Fields you’ve created on the same instance of [`fields`](dlocal.js-reference.md#dlocal-fields-options) to tokenize.
* `tokenData`, an object containing additional payment information you might have collected. In the case of cards, it can contain any of the following parameters:

| **Parameter** | **Type** | **Description** |
| --- | --- | --- | --- |
| `name` | String **\(Required\)** | Cardholder name |
| `address_line1 address_line2 address_city address_state address_zip address_country` | String \(Optional\) | Fields for billing address information. The **address\_country** field is a two character country code \(for example, `'BR'`\). |
| `currency` | String \(Optional\) | Currency of the transaction  |

`dlocal.createToken` returns a `Promise` which resolves with a `result` object. This object has either:

* `result.token`: a Token was created successfully.
* `result.error`: there was an error. This includes client-side validation errors.

## The Fields Object

### `fields.create(type, options)` 

```javascript
var card = fields.create('card');
```

This method creates an instance of a specific Field. It takes the`type` of Field to create as well as an `options` object.

### **Field Types** 

| **Type** | **Description** |
| --- | --- | --- | --- | --- |
| `card` | A flexible single-line input that collects cardNumber, cardExpiry and cardCvc. |
| ~~`cardNumber`~~ | The card number. **\(Coming Soon\)** |
| ~~`cardExpiry`~~ | The card‘s expiration date. **\(Coming Soon\)** |
| ~~`cardCvc`~~ | The card‘s CVC number. **\(Coming Soon\)** |

{% hint style="info" %}
The the moment, only the [`card`](fields-setup-guide.md) type of Field is available. In the near future we will also provide separate Fields for cardNumber, cardExpiry and cardCvc. In any case, we highly recommend to continue to use the `card` Fields, as it provides a better user experience.
{% endhint %}

### **Field Options** 

All Elements accept a common set of options, and then some Field-specific options.

#### Common options:

| **Option** | **Type** | **Description** |
| --- | --- | --- |
| classes | Object \(Optional\) | Set custom class names on the container DOM element when the dLocal Field is in a particular state. |
| style | Object \(Optional\) | Customize appearance using CSS properties. Style is specified as an object for any of the variants below.For each of the above, the properties below can be customized.The following pseudo-classes and pseudo-elements can also be styled with the above properties, as a nested object inside the variant. |

#### **Options available exclusively to the `card` Field:**

| **Option** | **Type** | **Description** |
| --- | --- | --- | --- | --- |
| value | Object \(Optional\) | A pre-filled set of values to include in the input \(e.g., `{postalCode: '94110'}`\). Note that sensitive card information \(card number, CVC, and expiration date\) cannot be pre-filled. |
| iconStyle | String \(Optional\) | Appearance of the icon in the Element. Either `'solid'` or `'default'`. |
| hideIcon | Boolean \(Optional\) | Hides the icon in the Element. Default is `false`. |
| disabled | Boolean \(Optional\) | Applies a disabled state to the Element such that user input is not accepted. Default is `false`. |

## The Field

### `field.mount(domElement)` 

You need to create a container DOM element to mount a Field. If the container DOM element has a label, the Field is automatically focused when its label is clicked. There are two ways to do this:

1. Mount the instance within a `<label>`.

   ```markup
   <label>Card
     <div id="card-field"></div>
   </label>
   ```

2. Create a `<label>` with a `for` attribute, referencing the ID of your container.

   ```markup
   <label for="card-field">Card</label>
   <div id="card-field"></div>
   ```

The `field.mount()` method attaches your element to the DOM. `field.mount()` accepts either a CSS Selector \(e.g., `'#card-element'`\) or a DOM element.

```javascript
cardField.mount('#card-field');
```

### `field.on(event, handler)` 

The only way to communicate with your Field is by listening to an `event`. Fields might emit any of the events below. All events have a payload object that has an `fieldType` property with the [type](https://stripe.com/docs/stripe-js/reference#element-types) of the Field that emitted the event.

| **Event** | **Description** |
| --- | --- | --- |
| blur | Triggered when the Field loses focus. |
| change | Triggered when any of the following values changes on the Field. The event payload always contains certain keys, in addition to some Field-specific keys. |

### Input validation

Fields validates customer input as it is typed. To help your customers catch mistakes, listen to `change`events on the Field and display any errors:

```javascript
card.addEventListener('change', function(event) {
  var displayError = document.getElementById('card-errors');
  if (event.error) {
    displayError.textContent = event.error.message;
  } else {
    displayError.textContent = '';
  }
});
```

### Other Methods

| **Method** | **Description** |
| --- | --- | --- | --- | --- | --- | --- |
| `blur()` | Blurs the Field |
| `clear()` | Clears the value\(s\) of the Field. |
| `destroy()` | Removes the Field from the DOM and destroys it. Note: a destroyed Field cannot be re-activated or re-mounted to the DOM. |
| `focus()` | Focuses the Field. |
| `unmount()` | Unmounts the Field from the DOM. Call [field.mount\(\)](dlocal.js-reference.md#field-mount-domelement) to re-attach it to the DOM. |
| `update(options)` | Updates the options the Field was initialized with. Updates are merged into the existing configuration. Accepts the same options as [fields.create\(\)](dlocal.js-reference.md#fields-create-type-options). |

If you collect certain information in a different part of your interface \(e.g., postal code\), use `update()`with the appropriate information.

```javascript
var myPostalCodeField = document.querySelector('input[name="my-postal-code"]');
myPostalCodeField.addEventListener('change', function(event) {
  card.update({value: {postalCode: event.target.value}});
});
```

The styles of a Field can be dynamically changed using `update()`. This method can be used to simulate CSS media queries that automatically adjust the size of Fields when viewed on different devices.

```javascript
window.addEventListener('resize', function(event) {
  if (window.innerWidth <= 320) {
    card.update({style: {base: {fontSize: '13px'}}});
  } else {
    card.update({style: {base: {fontSize: '16px'}}});
  }
});

var previousBrand;
card.on('change', function(event) {
  if (event.brand !== previousBrand && event.brand === 'mastercard') {
    card.update({style: {base: {color: 'orange'}}});
    previousBrand = event.brand;
  }
});
```

## The Field container

Style the container you mount a Field to as if it were an `<input>` on your page. For example, to control `padding` and `border` on a Field, set these properties on the container. This is usually done by re-using the classes that you have applied to your DOM `<input>` elements. Example:

```markup
<style>
  .my-input {
    padding: 10px;
    border: 1px solid #ccc;
  }
</style>

<form>
  <div>
    <label>Name</label>
    <input class="my-input">
  </div>
  <div>
    <label>Card</label>
    <!-- Using the same "my-input" class on the -->
    <!-- regular input above and on this container. -->
    <div class="my-input" id="card-field"></div>
  </div>
</form>
```

After the Field is mounted, the `.DlocalField` class is added to the container. Additionally, the following classes are automatically added to the container when the Element is complete, empty, focused, invalid, or autofilled by the browser:

* `.DlocalField--complete`
* `.DlocalField--empty`
* `.DlocalField--focus`
* `.DlocalField--invalid`
* `.DlocalField--autofilled` \(Chrome and Safari only\)

These class names can be customized using the `classes` [option](dlocal.js-reference.md#field-options) when you create an Element.

## Supported browsers

dLocal.js strives to support all recent versions of major browsers. For the sake of security and providing the best experience to the majority of customers, we do not support browsers that are no longer receiving security updates and represent a small minority of traffic.

* We support Chrome and Safari on all platforms and Firefox on desktop platforms.
* We support Internet Explorer and Edge per [Microsoft's lifecycle policy](https://support.microsoft.com/en-us/gp/microsoft-internet-explorer). As of January 12, 2016, we support Internet Explorer 9 and above.
* We support the Android native browser on Android 4.4 and later.
* We require TLS 1.2 to be supported by the browser.

If you have an issue with dLocal.js on a specific browser, please contact us so we can improve its support.

