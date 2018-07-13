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



