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
| fonts | Array \(Optional\) | An array of custom fonts, which Elements created from the `elements` object can use.  Fonts can either be loaded via a CSS file by passing an object with the [cssSrc attribute](dlocal.js-reference.md#the-csssrc-attribute), **or** they can be loaded directly by passing a [Font object](dlocal.js-reference.md#the-font-object). |
| locale | String | The [IETF language tag](https://en.wikipedia.org/wiki/IETF_language_tag) of the locale to display placeholders and error strings in. Default is Spanish`(es)`. Supported values are: **es, en, pt, zh, cv, tr.** |

#### The cssSrc attribute

| **Parameter** | **Type** | **Description** |
| --- | --- |
| cssSrc | String | A relative or absolute URL pointing to a CSS file with [@font-face](https://developer.mozilla.org/en/docs/Web/CSS/@font-face) definitions, for example:  `"https://fonts.googleapis.com/css?family=Open+Sans"`  |

#### The Font object

| Parameter | Type | Description |
| --- | --- | --- | --- | --- | --- | --- |
| family | String | The name to give the font. |
| src | String | A valid [src ](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/src)value pointing to your custom font file. This is usually \(though not always\) a link to a file with a `.woff`, `.otf`, or `.svg` suffix. |
| display | String \(Optional\) | A valid [font-display ](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display)value. |
| style | String | One of `'normal'`, `'italic'`, `'oblique'`. Defaults to `'normal'`. |
| unicodeRange | String \(Optional\) | A valid [unicode-range ](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/unicode-range)value. |
| weight | String \(Optional\) | A valid [font-weight ](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight). Note that this is a string, not a number. |

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
| name | String **\(Required\)** | Cardholder name |
| address\_line1 address\_line2 address\_city address\_state address\_zip address\_country | String \(Optional\) | Fields for billing address information. The **address\_country** field is a two character country code \(for example, `'BR'`\). |
| currency | String \(Optional\) | Currency of the transaction  |

`dlocal.createToken` returns a `Promise` which resolves with a `result` object. This object has either:

* `result.token`: a Token was created successfully.
* `result.error`: there was an error. This includes client-side validation errors.

## The Fields Object



