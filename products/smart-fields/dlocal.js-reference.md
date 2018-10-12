# dlocal.js Reference

### Including dlocal.js

However you’re using dlocal.js, you always begin by including the library and setting your API key. To get started, include this script on your pages—it should always be loaded directly from [https://js.dlocal.com](https://js.dlocal.com)**.** For testing purposes, you can use [https://js-sandbox.dlocal.com](https://js-sandbox.dlocal.com)**.**

```text
<script src="https://js.dlocal.com/"></script>
```

## The dLocal Object

* [**dlocal.fields\(\)**](dlocal.js-reference.md#dlocal-fields-options)
* [**dlocal.create\(\)**](dlocal.js-reference.md#the-field-object)
* [**dlocal.createToken\(\)**](dlocal.js-reference.md#dlocal-createtoken-field-tokendata)
* [**dlocal.createInstallmentsPlan\(\)**](dlocal.js-reference.md#dlocal-createinstallmentsplan-field-amount-currency)

### `dlocal.fields([options])`

Create pre-built UI components to collect payment information with [Smart Fields](./) \(simply referred to as `fields`in the API\).

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
| `fonts` | Array \(Optional\) | An array of custom fonts, which Smart Fields created from the `fields` object can use.  Fonts can either be loaded via a CSS file by passing an object with the [cssSrc attribute](dlocal.js-reference.md#the-csssrc-attribute), **or** they can be loaded directly by passing a [Font object](dlocal.js-reference.md#the-font-object). |

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

### `dlocal.createToken(field, tokenData)`

Use `dlocal.createToken()` to convert information collected by Smart Fields into a token that you safely pass to your server to use in an API call. **This token expires 10 minutes after it has been created**, so you need to make sure that the payment is made within that timeframe.

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
| `currency` | String \(Optional\) | Currency of the transaction |

`dlocal.createToken` returns a `Promise` which resolves with a `result` object. This object has either:

* `result.token`: a Token was created successfully.
* `result.error`: there was an error. This includes client-side validation errors.

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
      <td style="text-align:left">placeholder</td>
      <td style="text-align:left">String or obj</td>
      <td style="text-align:left">
        <p>Set custom placeholder for Field. For <code>number</code>, <code>expiration</code> or <code>cvv</code> Fields
          this option is a <code>string</code> with the corresponding placeholder value,
          if the Field is a <code>card</code> this option is an <code>object</code> with
          the corresponding placeholder value for each input:</p>
        <p><code>{</code>
        </p>
        <p> <code>cvv: &quot;cvv placeholder&quot;,</code>
        </p>
        <p> <code>number: &quot;number placeholder&quot;,</code>
        </p>
        <p> <code>expiration: &quot;expiration placeholder&quot;</code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">classes</td>
      <td style="text-align:left">Object (Optional)</td>
      <td style="text-align:left">
        <p>Set custom class names on the container DOM element when the dLocal Field
          is in a particular state.</p>
        <ul>
          <li><code>base</code> - The base class applied to the container.
            <br />Defaults to <b>DlocalField</b>.</li>
          <li><code>complete</code>- The class name to apply when the Field is complete.
            <br
            />Defaults to <b>DlocalField--complete</b>.</li>
          <li><code>empty</code> - The class name to apply when the Field is empty.
            <br
            />Defaults to <b>DlocalField--empty</b>.</li>
          <li><code>focus</code> - The class name to apply when the Field is focused.
            <br
            />Defaults to <b>DlocalField--focus</b>.</li>
          <li><code>invalid</code> - The class name to apply when the Field is invalid.
            <br
            />Defaults to <b>DlocalField--invalid</b>.</li>
          <li><code>webkitAutofill</code> - The class name to apply when the Field has
            its value autofilled by the browser (only on Chrome and Safari).
            <br />Defaults to <b>DlocalField--autofilled</b>.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">style</td>
      <td style="text-align:left">Object (Optional)</td>
      <td style="text-align:left">
        <p>Customize appearance using CSS properties. Style is specified as an object
          for any of the variants below.</p>
        <ul>
          <li><code>base</code>, base style—all other variants inherit from this style</li>
          <li><code>complete</code>, applied when the Field has valid input</li>
          <li><code>empty</code>, applied when the Field has no customer input</li>
          <li><code>invalid</code>, applied when the Field has invalid input</li>
          <li><code>autofilled</code>, applied when the Field is autofilled</li>
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
            across browsers, consider using a padding on the Field's container instead.</li>
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
          <li><code>:focus</code>
          </li>
          <li><code>::placeholder</code>
          </li>
          <li><code>::selection</code>
          </li>
          <li><code>:disabled</code>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>\#\#\#\# \*\*Options available exclusively to the \`card\` or \`number\` Field:\*\* \| \*\*Option\*\* \| \*\*Type\*\* \| \*\*Description\*\* \| \| :--- \| :--- \| :--- \| \| iconStyle \| String \\(Optional\\) \| Appearance of the icon in the Field. Either \`'solid'\` or \`'default'\`. \| \| hideIcon \| Boolean \\(Optional\\) \| Hides the icon in the Field. Default is \`false\`. \| \#\# The Field Object \* \\*\\*\\*\\*\[\*\*field.mount\\(\\)\*\*\]\(dlocal.js-reference.md\#field-mount-domelement\)\\*\\*\\*\\* \* \\*\\*\\*\\*\[\*\*field.on\\(\\)\*\*\]\(dlocal.js-reference.md\#field-on-event-handler\)\\*\\*\\*\\* \* \\*\\*\\*\\*\[\*\*Other methods\*\*\]\(dlocal.js-reference.md\#other-methods\)\\*\\*\\*\\* \* blur\\(\\) \* clear\\(\\) \* destroy\\(\\) \* focus\\(\\) \* unmount\\(\\) \* update\\(\\) \#\#\# \`field.mount\(domElement\)\` You need to create a container DOM element to mount a Smart Field. If the container DOM element has a label, the Field is automatically focused when its label is clicked. There are two ways to do this: 1. Mount the instance within a \`\`. \`\`\`markup Card \`\`\` 2. Create a \`\` with a \`for\` attribute, referencing the ID of your container. \`\`\`markup Card \`\`\` The \`field.mount\(\)\` method attaches your Field to the DOM. \`field.mount\(\)\` accepts either a CSS Selector \\(e.g., \`'\#card-field'\`\\) or a DOM element. \`\`\`javascript cardField.mount\('\#card-field'\); \`\`\` \#\#\# \`field.on\(event, handler\)\` The only way to communicate with your Smart Field is by listening to an \`event\`. Fields might emit any of the events below. All events have a payload object that has an \`fieldType\` property with the \[type\]\(https://stripe.com/docs/stripe-js/reference\#element-types\) of the Field that emitted the event.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Event</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">blur</td>
      <td style="text-align:left">
        <p>Triggered when any of the Fields elements loses focus. The event payload
          always contains certain keys:</p>
        <ul>
          <li><code>empty</code> - Boolean - <b><code>true</code></b> if the value is empty.</li>
          <li><code>complete</code> - Boolean -<b><code>true</code></b> if the value is
            well-formed and complete<b>:</b>
            <ul>
              <li><code>complete</code> can be used to progressively disclose the next parts
                of your form or to enable form submission.</li>
              <li><code>complete</code> is not an indicator of whether a customer is done
                with their input—it only indicates that the Field contains a complete,
                well-formed value.</li>
            </ul>
          </li>
          <li><code>error</code> - The current validation error, if any. Comprised of <code>message</code>, <code>code</code>,
            and <code>type</code> set to <code>validation_error</code>.</li>
          <li><code>brand</code> - String - The detected card brand, if any.</li>
          <li><code>element</code> - String - The name of the field that triggered the
            event: <code>&apos;number&apos;</code>, <code>&apos;expiration&apos;</code>, <code>&apos;cvv&apos;</code>.</li>
          <li><code>hasFocus</code> - Boolean - <b><code>true</code></b> if any of the
            Fields elements has focus (always false in <code>pan</code>, <code>expiration</code> and <code>cvv</code> Fields).</li>
          <li><code>autofilled</code> - Boolean - <b><code>true</code></b> if any of the
            Fields is autofilled.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">focus</td>
      <td style="text-align:left">
        <p>Triggered when any of the Fields elements gains focus. The event payload
          always contains certain keys:</p>
        <ul>
          <li><code>empty</code> - Boolean - <b><code>true</code></b> if the value is empty.</li>
          <li><code>complete</code> - Boolean -<b><code>true</code></b> if the value is
            well-formed and complete<b>:</b>
            <ul>
              <li><code>complete</code> can be used to progressively disclose the next parts
                of your form or to enable form submission.</li>
              <li><code>complete</code> is not an indicator of whether a customer is done
                with their input—it only indicates that the Field contains a complete,
                well-formed value.</li>
            </ul>
          </li>
          <li><code>error</code> - The current validation error, if any. Comprised of <code>message</code>, <code>code</code>,
            and <code>type</code> set to <code>validation_error</code>.</li>
          <li><code>brand</code> - String - The detected card brand, if any.</li>
          <li><code>element</code> - String - The name of the field that triggered the
            event: <code>&apos;number&apos;</code>, <code>&apos;expiration&apos;</code>, <code>&apos;cvv&apos;</code>.</li>
          <li><code>autofilled</code> - Boolean - <b><code>true</code></b> if any of the
            Fields is autofilled.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">error</td>
      <td style="text-align:left">Triggered when a client-side validation error is detected. The event payload
        always contains <code>error</code> key which contains the current validation
        error. Comprised of: <code>message</code>, <code>code</code> and <code>type</code>,
        set to <code>validation_error</code>.</td>
    </tr>
    <tr>
      <td style="text-align:left">complete</td>
      <td style="text-align:left">Triggered when the Field changes it's complete status. The event payload
        always contains<code>complete</code> - Boolean - key, which is <code>true</code> when
        the Field is complete and well-formed, and <code>false</code> otherwise.</td>
    </tr>
    <tr>
      <td style="text-align:left">empty</td>
      <td style="text-align:left">Triggered when the Field changes it's empty status. The event payload
        always contains <code>empty</code> - <code>Boolean</code> - key, which is <code>true</code> when
        the Field is empty, and <code>false</code> otherwise.</td>
    </tr>
    <tr>
      <td style="text-align:left">ready</td>
      <td style="text-align:left">Triggered when the Field is mounted and loaded in the DOM.</td>
    </tr>
    <tr>
      <td style="text-align:left">change</td>
      <td style="text-align:left">
        <p>Triggered when any of the following values changes on the Field. The event
          payload always contains certain keys, in addition to some Field-specific
          keys.</p>
        <ul>
          <li><code>empty</code> - Boolean - <b><code>true</code></b> if the value is empty.</li>
          <li><code>complete</code> - Boolean -<b><code>true</code></b> if the value is
            well-formed and complete<b>:</b>
            <ul>
              <li><code>complete</code> can be used to progressively disclose the next parts
                of your form or to enable form submission.</li>
              <li><code>complete</code>  <em>is not</em> an indicator of whether a customer
                is done with their input—it only indicates that the Field contains a complete,
                well-formed value.</li>
            </ul>
          </li>
          <li><code>error</code> - The current validation error, if any. Comprised of <code>message</code>, <code>code</code>,
            and <code>type</code> set to <code>validation_error</code>.</li>
          <li><code>brand</code> - The detected card brand, if any.</li>
          <li><code>autofilled</code> - Boolean - <b><code>true</code></b> if any of the
            Fields is autofilled.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">brand</td>
      <td style="text-align:left">Triggered when the Field detects a change in the card brand. This event
        can only be listened in <code>number</code> and <code>card</code> Smart Fields
        (it wont work in <code>cvv</code> and <code>expiration</code> Fields). The
        event payload always contains <code>brand</code> - String - key, which has
        the name of the detected brand if any, <code>null</code> otherwise.</td>
    </tr>
    <tr>
      <td style="text-align:left">autofilled</td>
      <td style="text-align:left">Triggered when the Field detects a change in it's autofilled status. The
        event payload always contains <code>autofilled</code> - Boolean - key, which
        is <b><code>true</code></b> if the field is autofilled.</td>
    </tr>
  </tbody>
</table>### Input validation

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
| `update(options)` | Updates the options the Field was initialized with. Updates are merged into the existing configuration. Accepts the same options as [fields.create\(\)](dlocal.js-reference.md#fields-create-type-options). |

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

