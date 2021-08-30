# dlocal.js Issuing Reference

### Including dlocal.js

However you’re using dlocal.js, you always begin by including the library and setting your API key. To get started, include this script on your pages—it should always be loaded directly from [https://js.dlocal.com](https://js.dlocal.com)**.** For testing purposes, you can use [https://js-sandbox.dlocal.com](https://js-sandbox.dlocal.com)**.**

```php
<script src="https://js.dlocal.com/"></script>
```

## The dLocal Object

* [dlocal.fields\(\)](../../../products/smart-fields/dlocal.js-reference.md#dlocal-fields-options)
* [dlocal.create\(\)](../../../products/smart-fields/dlocal.js-reference.md#the-field-object)

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
| `locale` | String | The [IETF language tag](https://en.wikipedia.org/wiki/IETF_language_tag) of the locale to display placeholders and error strings in. Default is Spanish`(es)`. Supported values are: **es, en, pt, zh, cv, tr.** |
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
| `weight` | String \(Optional\) | A valid [font-weight ](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight). Note that this is a string, not a number. |

## The Fields Object

* [fields.create\(\)](../../../products/smart-fields/dlocal.js-reference.md#fields-create-type-options)

### `fields.create(type, options)`

```javascript
var card = fields.create('card');
```

This method creates an instance of a specific Smart Field. It takes the`type` of Smart Field to create as well as an `options` object.

### **Smart Field Types** 

#### **Virtual Card**

**Countries where return an image**

Available in: Colombia.

| **Type** | **Description** |
| :--- | :--- |
| `read-only-card` | The virtual card front and rear pictures.  |

**Countries where return data**

| **Type** | **Description** |
| :--- | :--- |
| `read-only-pan` | The card’s PAN. |
| `read-only-expiration` | The card’s expiration date. |
| `read-only-cvv` | The card’s CVV2. |

### **Field Options**

All Smart Fields accept a common set of options, and then some Field-specific options.

#### Common options:

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
      <td style="text-align:left">Object (Optional)</td>
      <td style="text-align:left">
        <p>Set custom class names on the container DOM element when the dLocal Field
          is in a particular state.</p>
        <ul>
          <li><code>base</code> - The base class applied to the container.
            <br />Defaults to <b>DlocalField</b>.</li>
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
  </tbody>
</table>

_Note:_ **"read-only-card"** Smart Field Type ****only support lineHight style. 

## The Field Object

* [field.mount\(\)](dlocal.js-reference.md#field-mount-domelement)

### `field.mount(domElement)`

You need to create a container DOM element to mount a Smart Field. 

```markup
<div id="virtual-card-field"></div>
```

The field.mount\(\) method attaches your Field to the DOM. field.mount\(\) accepts either a CSS Selector \(e.g., '\#card-field'\) or a DOM element.

```javascript
cardField.mount('#virtual-card-field');
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

After the Field is mounted, the `.DlocalField` class is added to the container. 

## Supported browsers

dLocal.js strives to support all recent versions of major browsers. For the sake of security and providing the best experience to the majority of customers, we do not support browsers that are no longer receiving security updates and represent a small minority of traffic.

* We support Chrome and Safari on all platforms and Firefox on desktop platforms.
* We support Internet Explorer and Edge per [Microsoft's lifecycle policy](https://support.microsoft.com/en-us/gp/microsoft-internet-explorer). As of January 12, 2016, we support Internet Explorer 9 and above.
* We support the Android native browser on Android 4.4 and later.
* We require TLS 1.2 to be supported by the browser.

If you have an issue with dLocal.js on a specific browser, please contact us so we can improve its support.

