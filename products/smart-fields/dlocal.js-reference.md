# dlocal.js Reference

### Including dlocal.js

However you’re using dlocal.js, you always begin by including the library and setting your API key. To get started, include this script on your pages—it should always be loaded directly from **https://js.dlocal.com.** For testing purposes, you can use **https://js-sandbox.dlocal.com.**

```text
<script src="https://js.dlocal.com/"></script>
```

## The dLocal Object

* \*\*\*\*[**dlocal.fields\(\)**](dlocal.js-reference.md#dlocal-fields-options)\*\*\*\*
* \*\*\*\*[**dlocal.createToken\(\)**](dlocal.js-reference.md#dlocal-createtoken-field-tokendata)\*\*\*\*
* **dlocal.createInstallmentsPlan\(\)**

### `dlocal.fields([`_`options`_`])` 

Create pre-built UI components to collect payment information with [Smart Fields](./) \(simply referred to as `fields`in the API\).

```javascript
var fields = dlocal.fields({
            locale: 'en',
            country: 'BR'
        });
```

This method creates an instance of `fields`, which manages a group of Smart Fields. It receives an  options object. Available options are documented below:

| **Option** | **Type** | **Description** |
| :--- | :--- | :--- |
| `locale` | String | The [IETF language tag](https://en.wikipedia.org/wiki/IETF_language_tag) of the locale to display placeholders and error strings in. Default is Spanish`(es)`. Supported values are: **es, en, pt, zh, cv, tr.** |
| `country` | String | User’s country code. ISO 3166-1 alpha-2 codes. |
| `fonts` | Array \(Optional\) | An array of custom fonts, which Smart Fields created from the `fields` object can use.  Fonts can either be loaded via a CSS file by passing an object with the [cssSrc attribute](dlocal.js-reference.md#the-csssrc-attribute), **or** they can be loaded directly by passing a [Font object](dlocal.js-reference.md#the-font-object). |

| **Parameter** | **Type** | **Description** |
| :--- | :--- | :--- |
| `cssSrc` | String | A relative or absolute URL pointing to a CSS file with [@font-face](https://developer.mozilla.org/en/docs/Web/CSS/@font-face) definitions, for example:  `"https://fonts.googleapis.com/css?family=Open+Sans"`  |

#### The Font object

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `family` | String | The name to give the font. |
| `src` | String | A valid [src ](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/src)value pointing to your custom font file. This is usually \(though not always\) a link to a file with a `.woff`, `.otf`, or `.svg` suffix. |
| `display` | String \(Optional\) | A valid [font-display ](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display)value. |
| `style` | String | One of `'normal'`, `'italic'`, `'oblique'`. Defaults to `'normal'`. |
| `unicodeRange` | String \(Optional\) | A valid [unicode-range ](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/unicode-range)value. |
| `weight` | String \(Optional\) | A valid [font-weight ](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight). Note that this is a string, not a number. |

### `dlocal.createToken(field, tokenData)` 

Use `dlocal.createToken()` to convert information collected by Smart Fields into a  token that you safely pass to your server to use in an API call. **This token expires 10 minutes after it has been created**, so you need to make sure that the payment is made within that timeframe.

```javascript
dlocal.createToken(card,tokenData)
.then(function(result) {
  // Handle result.token
}
.catch(function(result) {
  // Handle result.error
}););
```

This method takes two arguments.

* `field`, the Smart Field you wish to tokenize data from. If applicable, the Smart Field pulls data from other Smart Fields you’ve created on the same instance of [`fields`](dlocal.js-reference.md#dlocal-fields-options) to tokenize.
* `tokenData`, an object containing additional payment information you might have collected. In the case of cards, it can contain any of the following parameters:

| **Parameter** | **Type** | **Description** |
| :--- | :--- | :--- |
| `name` | String **\(Required\)** | Cardholder name |
| `address_line1 address_line2 address_city address_state address_zip address_country` | String \(Optional\) | Fields for billing address information. The **address\_country** field is a two character country code \(for example, `'BR'`\). |
| `currency` | String \(Optional\) | Currency of the transaction  |

`dlocal.createToken` returns a `Promise` which resolves with a `result` object. This object has either:

* `result.token`: a Token was created successfully.
* `result.error`: there was an error. This includes client-side validation errors.

### `dlocal.createInstallmentsPlan(field, amount, currency)`

Use `dlocal.createInstallmentsPlan(field, amount, currency)`to specify an installment plan, to guarantee the surcharge per installment that will be charged.

```javascript
dlocal.createInstallmentsPlan(card, amount, currency)
.then(function(result) {
  // Handle result.installments
}
.catch(function(result) {
  // Handle result.error
}););
```

{% tabs %}
{% tab title="Installments Arguments" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| `field` | SmartField | The Smart Field you wish to create the installments plan, if you are not using a `card` Field we recommend to use `number` Field to create installments, but any of the Fields will work. |
| `amount` | Positive Float | The amount of the installments plan. |
| `currency` | String | The currency of the installments plan. |
{% endtab %}

{% tab title="Installments Plan Object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | String | The installments plan id. |
| `country` | String | The country of the installments plan \(this is the same you specified when you created the field\). |
| `currency` | String | The currency of the installments plan. |
| `bin` | String | The credit card bin. |
| `amount` | Positive Float | The amount of the installments plan. |
| `installments` | ​[Installment Object](https://docs.dlocal.com/api-documentation/payins-api-reference/installments#the-installment-object)\[ \] | The installments plan information |
{% endtab %}

{% tab title="Installment Object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | String | The installment id. |
| `installment_amount` | Positive Float | Installment amount. |
| `total_amount` | Positive Float | Installments total amount. |
| `installments` | Integer | Number of installments. |
{% endtab %}

{% tab title="Example Installments Plan Object" %}
```javascript
{
    "id" : "INS54434",
    "country" : "BR",
    "currency" : "BRL",
    "bin" : "435921",
    "amount": 1500,
    "installments" : [
        {
            "id" : "INS54434-3",
            "installment_amount" : 550,
            "installments" : 3,
            "total_amount" : 1650
        },
        {
            "id" : "INS54434-6",
            "installment_amount" : 350,
            "installments" : 6,
            "total_amount" : 2100
        },
        {
            "id" : "INS54434-8",
            "installment_amount" : 250,
            "installments" : 12,
            "total_amount" : 3000
        }
    ]
}
```
{% endtab %}
{% endtabs %}

## The Fields Object

* \*\*\*\*[**fields.create\(\)**](dlocal.js-reference.md#fields-create-type-options)\*\*\*\*

### `fields.create(type, options)` 

```javascript
var card = fields.create('card');
```

This method creates an instance of a specific Smart Field. It takes the`type` of Smart Field to create as well as an `options` object.

### **Smart Field Types** 

| **Type** | **Description** |
| :--- | :--- |
| `card` | A flexible single-line input that collects cardNumber, cardExpiry and cardCvc. **\(Recommended\)** |
| `pan` | The card‘s number.  |
| `expiration` | The card‘s expiration date.  |
| `cvv` | The card‘s CVC number.  |

{% hint style="info" %}
We highly recommend to use the `card` Field, as it provides a better user experience.
{% endhint %}

### **Field Options** 

All Smart Fields accept a common set of options, and then some Field-specific options.

#### Common options:

| **Option** | **Type** | **Description** |
| :--- | :--- | :--- |
| classes | Object \(Optional\) | Set custom class names on the container DOM element when the dLocal Field is in a particular state. |
| style | Object \(Optional\) | Customize appearance using CSS properties. Style is specified as an object for any of the variants below.For each of the above, the properties below can be customized.The following pseudo-classes and pseudo-elements can also be styled with the above properties, as a nested object inside the variant. |

#### **Options available exclusively to the `card` Field:**

| **Option** | **Type** | **Description** |
| :--- | :--- | :--- |
| value | Object \(Optional\) | A pre-filled set of values to include in the input \(e.g., `{postalCode: '94110'}`\). Note that sensitive card information \(card number, CVC, and expiration date\) cannot be pre-filled. |
| iconStyle | String \(Optional\) | Appearance of the icon in the Field. Either `'solid'` or `'default'`. |
| hideIcon | Boolean \(Optional\) | Hides the icon in the Field. Default is `false`. |
| disabled | Boolean \(Optional\) | Applies a disabled state to the Field such that user input is not accepted. Default is `false`. |

## The Field Object

* \*\*\*\*[**field.mount\(\)**](dlocal.js-reference.md#field-mount-domelement)\*\*\*\*
* \*\*\*\*[**field.on\(\)**](dlocal.js-reference.md#field-on-event-handler)\*\*\*\*
* \*\*\*\*[**Other methods**](dlocal.js-reference.md#other-methods)\*\*\*\*
  * blur\(\)
  * clear\(\)
  * destroy\(\)
  * focus\(\)
  * unmount\(\)
  * update\(\)

### `field.mount(domElement)` 

You need to create a container DOM element to mount a Smart Field. If the container DOM element has a label, the Field is automatically focused when its label is clicked. There are two ways to do this:

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

The `field.mount()` method attaches your Field to the DOM. `field.mount()` accepts either a CSS Selector \(e.g., `'#card-field'`\) or a DOM element.

```javascript
cardField.mount('#card-field');
```

### `field.on(event, handler)` 

The only way to communicate with your Smart Field is by listening to an `event`. Fields might emit any of the events below. All events have a payload object that has an `fieldType` property with the [type](https://stripe.com/docs/stripe-js/reference#element-types) of the Field that emitted the event.

| **Event** | **Description** |
| :--- | :--- |
| blur | Triggered when any of the Fields elements loses focus. The event payload always contains certain keys: |
| focus | Triggered when any of the Fields elements gains focus. The event payload always contains certain keys:  |
| error | Triggered when a client-side validation error is detected. The event payload always contains `error` key which contains the current validation error. Comprised of: `message`,  `code` and `type`, set to `validation_error`. |
| complete | Triggered when the Field changes it's complete status. The event payload always contains`complete` - Boolean  - key, which is `true` when the Field is complete and well-formed, and `false` otherwise. |
| empty | Triggered when the Field changes it's empty status. The event payload always contains `empty` - `Boolean` - key, which is `true` when the Field is empty, and `false` otherwise. |
| ready | Triggered when the Field is mounted and loaded in the DOM. |
| change | Triggered when any of the following values changes on the Field. The event payload always contains certain keys, in addition to some Field-specific keys. |



### Input validation

Smart Fields validates customer input as it is typed. To help your customers catch mistakes, listen to `change`events on the Field and display any errors:

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
| :--- | :--- |
| `blur()` | Blurs the Field |
| `clear()` | Clears the value\(s\) of the Field. |
| `destroy()` | Removes the Field from the DOM and destroys it. Note: a destroyed Field cannot be re-activated or re-mounted to the DOM. |
| `focus()` | Focuses the Field. In a `card` Field it will focus in the `number` field. |
| `unmount()` | Unmounts the Field from the DOM. Call [field.mount\(\)](dlocal.js-reference.md#field-mount-domelement) to re-attach it to the DOM. |
| ~~_update\(options\)_~~ | ~~Updates the options the Field was initialized with. Updates are merged into the existing configuration. Accepts the same options as~~ [~~fields.create\(\)~~](dlocal.js-reference.md#fields-create-type-options)~~.~~ **\(Coming soon\)** |

The styles of a Smart Field can be dynamically changed using `update()`. This method can be used to simulate CSS media queries that automatically adjust the size of Fields when viewed on different devices.

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

Style the container you mount a Smart Field to, as if it were an `<input>` on your page. For example, to control `padding` and `border` on a Field, set these properties on the container. This is usually done by re-using the classes that you have applied to your DOM `<input>` elements. Example:

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

After the Field is mounted, the `.DlocalField` class is added to the container. Additionally, the following classes are automatically added to the container when the Field is complete, empty, focused, invalid, or autofilled by the browser:

* `.DlocalField--complete`
* `.DlocalField--empty`
* `.DlocalField--focus`
* `.DlocalField--invalid`
* `.DlocalField--autofilled` \(Chrome and Safari only\)

These class names can be customized using the `classes` [option](dlocal.js-reference.md#field-options) when you create a Smart Field.

## Supported browsers

dLocal.js strives to support all recent versions of major browsers. For the sake of security and providing the best experience to the majority of customers, we do not support browsers that are no longer receiving security updates and represent a small minority of traffic.

* We support Chrome and Safari on all platforms and Firefox on desktop platforms.
* We support Internet Explorer and Edge per [Microsoft's lifecycle policy](https://support.microsoft.com/en-us/gp/microsoft-internet-explorer). As of January 12, 2016, we support Internet Explorer 9 and above.
* We support the Android native browser on Android 4.4 and later.
* We require TLS 1.2 to be supported by the browser.

If you have an issue with dLocal.js on a specific browser, please contact us so we can improve its support.
