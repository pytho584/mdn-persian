---
title: CSSFontFeatureValuesRule
slug: Web/API/CSSFontFeatureValuesRule
page-type: web-api-interface
browser-compat: api.CSSFontFeatureValuesRule
---

{{APIRef("CSSOM")}}

رابط **`CSSFontFeatureValuesRule`** یک [قاعده-at](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) {{cssxref("@font-feature-values")}} را نمایش می‌دهد. مقادیر ویژگی‌های نمونه آن را می‌توان با استفاده از رابط [`CSSFontFeatureValuesMap`](/en-US/docs/Web/API/CSSFontFeatureValuesMap) به دست آورد.

`@font-feature-values` به توسعه‌دهندگان اجازه می‌دهد تا برای یک چهره قلم مشخص، یک نام خوانا برای انسان را با یک شاخص عددی که یک ویژگی [قلم OpenType](/en-US/docs/Web/CSS/Guides/Fonts/OpenType_fonts) خاص را کنترل می‌کند، مرتبط کنند.
برای ویژگی‌هایی که شکل‌واره‌های جایگزین را انتخاب می‌کنند (stylistic، styleset، character-variant، swash، ornament یا annotation)، ویژگی {{cssxref("font-variant-alternates")}} می‌تواند به نام خوانا برای انسان ارجاع دهد تا ویژگی مرتبط اعمال شود.
این کار راحت است، زیرا اجازه می‌دهد از یک نام یکسان برای نمایش مجموعه‌ای از شکل‌واره‌های جایگزین در چندین قلم استفاده شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از جد خود {{domxref("CSSRule")}} به ارث می‌برد._

- {{domxref("CSSFontFeatureValuesRule.annotation")}} {{experimental_inline}}
  - : یک تعریف و مقدار مقدار تعریف‌شده توسط کاربر که یک حاشیه‌نویسی جایگزین از قلم را اعمال می‌کند.
- {{domxref("CSSFontFeatureValuesRule.characterVariant")}} {{experimental_inline}}
  - : یک تعریف و مقدار مقدار تعریف‌شده توسط کاربر که جایگزین‌های سبکی برای کاراکترهای قلم اعمال می‌کند.
- {{domxref("CSSFontFeatureValuesRule.fontFamily")}}
  - : یک رشته که خانواده قلمی را که این قاعده به آن اعمال می‌شود، مشخص می‌کند.
- {{domxref("CSSFontFeatureValuesRule.ornaments")}} {{experimental_inline}}
  - : یک تعریف و مقدار مقدار تعریف‌شده توسط کاربر که تزئینات جایگزین قلم را اعمال می‌کند.
- {{domxref("CSSFontFeatureValuesRule.styleset")}} {{experimental_inline}}
  - : یک تعریف و مقدار مقدار تعریف‌شده توسط کاربر که مجموعه‌های سبک جایگزین قلم را اعمال می‌کند.
- {{domxref("CSSFontFeatureValuesRule.stylistic")}} {{experimental_inline}}
  - : یک تعریف و مقدار مقدار تعریف‌شده توسط کاربر که شکل‌واره‌های جایگزین قلم را اعمال می‌کند.
- {{domxref("CSSFontFeatureValuesRule.swash")}} {{experimental_inline}}
  - : یک تعریف و مقدار مقدار تعریف‌شده توسط کاربر که swashهای جایگزین قلم را اعمال می‌کند.

## روش‌های نمونه

_روش‌ها را از جد خود {{domxref("CSSRule")}} به ارث می‌برد._

## مثال‌ها

### خواندن خانواده قلم

در این مثال، ما دو {{cssxref("@font-feature-values")}} اعلام می‌کنیم: یکی برای خانواده قلم _Font One_ و دیگری برای _Font Two_.
در هر دو اعلام، ما تعریف می‌کنیم که نام "nice-style" می‌تواند برای نمایش شکل‌واره‌های جایگزین styleset برای هر دو قلم استفاده شود، و شاخص آن جایگزین را در هر خانواده قلم مشخص می‌کنیم.
سپس شکل‌واره‌های جایگزین برای هر کلاس `.nice-look` با استفاده از {{cssxref("font-variant-alternates")}} و ارسال نام به تابع [`styleset()`](/en-US/docs/Web/CSS/Reference/Properties/font-variant-alternates#styleset) اعمال می‌شوند.

سپس با استفاده از CSSOM این اعلام‌ها را به عنوان نمونه‌های `CSSFontFeatureValuesRule` می‌خوانیم و آنها را در لاگ نمایش می‌دهیم.

#### CSS

```css
/* قاعده-at برای "nice-style" در Font One */
@font-feature-values Font One {
  @styleset {
    nice-style: 12; /* نامی که برای نمایش مجموعه جایگزین شکل‌واره‌ها در شاخص 12 استفاده می‌شود */
  }
}

/* قاعده-at برای "nice-style" در Font Two */
@font-feature-values Font Two {
  @styleset {
    nice-style: 4;
  }
}

/* اعمال قواعد-at با یک اعلام واحد */
.nice-look {
  font-variant-alternates: styleset(
    nice-style
  ); /* نام، شاخص متفاوتی را برای همان جایگزین در قلم‌های مختلف انتخاب می‌کند */
}
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 40px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### JavaScript

```js
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const rules = document.getElementById("css-output").sheet.cssRules;

const fontOne = rules[0]; // یک CSSFontFeatureValuesRule
log(`خانواده قلم اول '@font-feature-values': "${fontOne.fontFamily}".`);

const fontTwo = rules[1]; // یک CSSFontFeatureValuesRule دیگر
log(`خانواده قلم دوم '@font-feature-values': "${fontTwo.fontFamily}"`);
```

{{EmbedLiveSample("read_font_family", "100%", "100px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("@font-feature-values")}}