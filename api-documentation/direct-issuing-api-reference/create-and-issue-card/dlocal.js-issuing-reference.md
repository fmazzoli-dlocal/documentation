---
description: Check the dLocal.js issuing reference.
---

# dLocal.js issuing reference

## Including dLocal.js

However you’re using dLocal.js, you always begin by including the library and setting your API key. To get started, include this script on your pages—it should always be loaded directly from [https://js.dlocal.com](https://js.dlocal.com)**.**

For testing purposes, you can use [https://js-sandbox.dlocal.com](https://js-sandbox.dlocal.com)**.**

```php
<script src="https://js.dlocal.com/"></script>
```

## The dLocal **o**bject

* [dlocal.fields\(\)](../../../products/smart-fields/dlocal.js-reference.md#dlocal-fields-options)
* [dlocal.createPinToken\(\)](dlocal.js-issuing-reference.md#dlocal-createpintoken-field)

### `dlocal.fields([options])`

Create pre-built UI components to collect payment information with [Smart Fields](../../../products/smart-fields/) \(simply referred to as `fields`in the API\).

```javascript
var fields = dlocal.fields({ 
    locale: 'en',
    country: 'BR'
});
```

This method creates an instance of `fields`, which manages a group of Smart Fields. It receives an options object. Available options are documented below:

| **Option** | **Type** | **Description** |
| :--- | :--- | :--- |
| `locale` | String | The [IETF language tag](https://en.wikipedia.org/wiki/IETF_language_tag) of the locale to display placeholders and error strings in. Default is Spanish`(es)`. Supported values are **es, en, pt, zh, cv, tr.** |
| `country` | String | User’s country code. ISO 3166-1 alpha-2 codes. |
| `fonts` | Array \(Optional\) | An array of custom fonts, which Smart Fields created from the `fields` object can use.  Fonts can either be loaded via a CSS file by passing an object with the [cssSrc attribute](../../../products/smart-fields/dlocal.js-reference.md#the-csssrc-attribute), **or** they can be loaded directly by passing a [Font object](../../../products/smart-fields/dlocal.js-reference.md#the-font-object). |

| **Parameter** | **Type** | **Description** |
| :--- | :--- | :--- |
| `cssSrc` | String | A relative or absolute URL pointing to a CSS file with [@font-face](https://developer.mozilla.org/en/docs/Web/CSS/@font-face) definitions, for example:  `"https://fonts.googleapis.com/css?family=Open+Sans"` |

#### The Font object

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `family` | String | The name to give the font. |
| `src` | String | A valid [src ](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/src)value pointing to your custom font file. This is usually \(though not always\) a link to a file with a `.woff`, `.otf`, or `.svg` suffix. |
| `display` | String \(Optional\) | A valid [font-display ](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display)value. |
| `style` | String | One of `'normal'`, `'italic'`, `'oblique'`. Defaults to `'normal'`. |
| `unicodeRange` | String \(Optional\) | A valid [unicode-range ](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/unicode-range)value. |
| `weight` | String \(Optional\) | A valid [font-weight](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight). Note that this is a string, not a number. |



### **`dlocal.createPinToken(field)`**

Use `dlocalInstance.createPinToken()` to convert information collected by Smart Fields into a token that you can safely pass to your server for use in an API call. 

{% hint style="warning" %}
This token expires 10 minutes after it has been created, or after the operation is made.
{% endhint %}

```javascript
dlocalInstance.createPinToken(field)
   .then(function(result) {
       // Handle result.token
   })
   .catch(function(result) {
       // Handle result.error
});
```

This method takes one argument.

* field, the Smart Field you wish to tokenize data from. If applicable, the Smart Field pulls data from other Smart Fields you’ve created on the same instance of fields to tokenize \(i.e: change pin operation\).

`dlocalInstance.createPinToken` returns a Promise which resolves with a result object. This object has either:

| Result | Description |
| :--- | :--- |
| result.token | Token was created successfully |
| result.error | There was an error. This includes client-side validation errors. |

## The Fields object

* [fields.create \(\)](dlocal.js-issuing-reference.md#fields-create-type-options)
* [field.mount \(\)](dlocal.js-issuing-reference.md#field-mount-domelement)
* [field.on\(\)](dlocal.js-issuing-reference.md#field-on-event-handler)

### `fields.create(type, options)`

```javascript
var card = fields.create('card');
```

This method creates an instance of a specific Smart Field. It takes the`type` of Smart Field to create as well as an `options` object.

### `field.mount(domElement)`

You need to create a container DOM element to mount a Smart Field. 

```markup
<div id="virtual-card-field"></div>
```

The `field.mount()` method attaches your Field to the DOM. `field.mount()` accepts either a CSS Selector \(e.g., '\#card-field'\) or a DOM element.

```javascript
cardField.mount('#virtual-card-field');
```

### **`field.on(event, handler)`**

The only way to communicate with your Smart Field is by listening to an event. Fields might emit any of the events below. All events have a payload object that has a fieldType property with the type of the Field that emitted the event.

| **Event** | **Description** |
| :--- | :--- |
| ready | Triggered when the Field is mounted and loaded in the DOM. |
| external-error | Triggered when an error occurs getting data from the server \(e.g: [virtual card data](https://docs.dlocal.com/api-documentation/direct-issuing-api-reference/create-and-issue-card/dlocal.js-issuing-reference#virtual-card)\). |

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

After the Field is mounted, the `.DlocalField` class is added to the container. 

## **Smart Field Types** 

### **Virtual Card**

#### **Countries where return an image**

| **Type** | **Description** |
| :--- | :--- |
| `read-only-card` | The virtual card front and rear pictures.  |

**Countries where return data**

| **Type** | **Description** |
| :--- | :--- |
| `read-only-pan` | The card’s PAN. |
| `read-only-expiration` | The card’s expiration date. |
| `read-only-cvv` | The card’s CVV2. |

### PIN

| **Type** | **Description** |
| :--- | :--- |
| `pin` | Allows cardholders to set their PIN code. |
| `new-pin` | Allows cardholders to set their new PIN code ****\(change PIN method\). |
| `old-pin` | Allows cardholders to enter their current PIN code \(change PIN method\). |

### **Field options**

All Smart Fields accept a common set of options, and then some field specific options.

#### Common options

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Option</b>
      </th>
      <th style="text-align:left"><b>Type</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">classes</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left">
        <p>Set custom class names on the container DOM element when the dLocal Field
          is in a particular state.</p>
        <ul>
          <li><code>base</code> - The base class applied to the container.
            <br />Defaults to <b>dLocalField</b>.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">style</td>
      <td style="text-align:left">Object (Optional)</td>
      <td style="text-align:left">
        <p></p>
        <p>Customize appearance using CSS properties. Style is specified as an object
          for any of the variants below.</p>
        <ul>
          <li><code>base</code>, base style&#x2014;all other variants inherit from this
            style</li>
        </ul>
        <p>For each of the above, the properties below can be customized.</p>
        <ul>
          <li><code>color</code>
          </li>
          <li><code>fontFamily</code>
          </li>
          <li><code>fontSize</code>
          </li>
          <li><code>fontSmoothing</code>
          </li>
          <li><code>fontStyle</code>
          </li>
          <li><code>fontVariant</code>
          </li>
          <li><code>iconColor</code>
          </li>
          <li><code>lineHeight</code>, to avoid cursors being rendered inconsistently
            across browsers, consider using a padding on the Field&apos;s container
            instead.</li>
          <li><code>letterSpacing</code>
          </li>
          <li><code>textDecoration</code>
          </li>
          <li><code>textShadow</code>
          </li>
          <li><code>textTransform</code>
          </li>
        </ul>
        <p>The following pseudo-classes and pseudo-elements can also be styled with
          the above properties, as a nested object inside the variant.</p>
        <ul>
          <li><code>:hover</code>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">maskInput</td>
      <td style="text-align:left">boolean (Optional)</td>
      <td style="text-align:left">Mask the value like an input type password.</td>
    </tr>
  </tbody>
</table>

{% hint style="info" %}
"read-only-card" Smart Field Type only supports lineHight style. 
{% endhint %}

## Supported browsers

dLocal.js strives to support all recent versions of major browsers. For the sake of security and providing the best experience to the majority of customers, we do not support browsers that are no longer receiving security updates and represent a small minority of traffic.

* We support Chrome and Safari on all platforms and Firefox on desktop platforms.
* We support Internet Explorer and Edge per [Microsoft's lifecycle policy](https://support.microsoft.com/en-us/gp/microsoft-internet-explorer). As of January 12, 2016, we support Internet Explorer 9 and above.
* We support the Android native browser on Android 4.4 and later.
* We require TLS 1.2 to be supported by the browser.

If you have an issue with dLocal.js on a specific browser, please contact us so we can improve its support.

