---
title: CSSFontFeatureValuesMap
slug: Web/API/CSSFontFeatureValuesMap
page-type: web-api-interface
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesMap
---

{{APIRef("CSSOM")}}{{SeeCompatTable}}

رابط **`CSSFontFeatureValuesMap`** در [مدل شیء CSS (CSSOM)](/en-US/docs/Web/API/CSS_Object_Model) مجموعه‌ای تکرارپذیر و فقط‌خواندنی از ویژگی‌های [CSSFontFeatureValuesRule](/en-US/docs/Web/API/CSSFontFeatureValuesRule) مانند [`swash`](/en-US/docs/Web/API/CSSFontFeatureValuesRule/swash)، [`annotation`](/en-US/docs/Web/API/CSSFontFeatureValuesRule/annotation)، [`ornaments`](/en-US/docs/Web/API/CSSFontFeatureValuesRule/ornaments) و غیره را نمایش می‌دهد.

یک نمونهٔ `CSSFontFeatureValuesMap` یک [شیء شبیه به Map](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map#map-like_browser_apis) فقط‌خواندنی است که در آن هر کلید، نام تعریف‌شده توسط کاربر برای ارجاع به یک ویژگی قلم است و مقدار متناظر، ایندکس آن ویژگی قلم درون فونت است.

## ویژگی‌های نمونه

- {{domxref('CSSFontFeatureValuesMap.size')}} {{experimental_inline}}
  - : یک عدد صحیح مثبت شامل اندازهٔ شیء `CSSFontFeatureValuesMap` را برمی‌گرداند.

## متدهای نمونه

- {{domxref('CSSFontFeatureValuesMap.clear()')}} {{experimental_inline}}
  - : تمام اعلان‌های موجود در `CSSFontFeatureValuesMap` را حذف می‌کند.
- {{domxref('CSSFontFeatureValuesMap.delete()')}} {{experimental_inline}}
  - : اعلان CSS مربوط به ویژگی داده‌شده را در `CSSFontFeatureValuesMap` حذف می‌کند.
- {{domxref('CSSFontFeatureValuesMap.entries()')}} {{experimental_inline}}
  - : یک شیء [تکرارگر Map](/en-US/docs/Web/API/CSSFontFeatureValuesMap/Symbol.iterator) جدید برمی‌گرداند که شامل جفت‌های `[key, value]` برای هر اعلان در این `CSSFontFeatureValuesMap` به ترتیب درج است.
- {{domxref('CSSFontFeatureValuesMap.forEach()')}} {{experimental_inline}}
  - : یک تابع داده‌شده را برای هر جفت کلید/مقدار در این `CSSFontFeatureValuesMap`، به ترتیب درج، یک‌بار اجرا می‌کند.
- {{domxref('CSSFontFeatureValuesMap.get()')}} {{experimental_inline}}
  - : مقدار متناظر با کلید را در این `CSSFontFeatureValuesMap` برمی‌گرداند، یا اگر وجود نداشته باشد، `undefined` را برمی‌گرداند.
- {{domxref('CSSFontFeatureValuesMap.has()')}} {{experimental_inline}}
  - : یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا ورودی با کلید مشخص‌شده در این `CSSFontFeatureValuesMap` وجود دارد یا خیر.
- {{domxref('CSSFontFeatureValuesMap.keys()')}} {{experimental_inline}}
  - : یک شیء [تکرارگر Map](/en-US/docs/Web/API/CSSFontFeatureValuesMap/Symbol.iterator) جدید برمی‌گرداند که شامل `key` برای هر اعلان در این `CSSFontFeatureValuesMap` به ترتیب درج است.
- {{domxref('CSSFontFeatureValuesMap.set()')}} {{experimental_inline}}
  - : یک ورودی جدید با کلید و مقدار مشخص‌شده به این `CSSFontFeatureValuesMap` اضافه می‌کند، یا اگر کلید از قبل وجود داشته باشد، ورودی موجود را به‌روزرسانی می‌کند.
- {{domxref('CSSFontFeatureValuesMap.values()')}} {{experimental_inline}}
  - : یک شیء [تکرارگر Map](/en-US/docs/Web/API/CSSFontFeatureValuesMap/Symbol.iterator) جدید برمی‌گرداند که شامل `value` برای هر اعلان در این `CSSFontFeatureValuesMap` به ترتیب درج است.
- [`CSSFontFeatureValuesMap.[Symbol.iterator]()`](/en-US/docs/Web/API/CSSFontFeatureValuesMap/Symbol.iterator)
  - : خود شیء تکرارگر را برمی‌گرداند. این امکان را فراهم می‌کند که اشیاء تکرارگر نیز تکرارپذیر باشند.

## نمونه‌ها

### Logging user-defined names

این مثال نشان می‌دهد که چگونه می‌توانید نام‌های تعریف‌شده توسط کاربر (و ایندکس نگاشت‌شدهٔ آن‌ها) را که در یک `CSSFontFeatureValuesMap` (برای ویژگی‌های خاص `CSSFontFeatureValuesRule`) ذخیره شده‌اند، ثبت (log) کنید.

#### CSS

ابتدا یک {{cssxref("@font-feature-values")}} برای خانوادهٔ فونت _Font One_ اعلان می‌کنیم. این شامل اعلان نام‌های «nice-style» و «odd-style» است که می‌توانند برای نمایش گلیف‌های جایگزین `styleset` برای _Font One_ استفاده شوند و مقادیر ایندکس آن گلیف‌های جایگزین را مشخص کنند. همچنین شامل اعلان نام «swishy» است که می‌تواند برای نمایش گلیف‌های جایگزین `swash` برای _Font One_ استفاده شود و ایندکس آن گلیف جایگزین را مشخص کند.

سپس گلیف‌های جایگزین «nice-style» برای هر کلاس `.nice-look` با استفاده از ویژگی {{CSSXRef("font-variant-alternates")}} و ارسال نام به تابع [`styleset()`](/en-US/docs/Web/CSS/Reference/Properties/font-variant-alternates#styleset) اعمال می‌شوند. همین کار برای نام «swishy» و گلیف‌های جایگزین `swash` انجام می‌شود و این نام به تابع [`swash()`](/en-US/docs/Web/CSS/Reference/Properties/font-variant-alternates#swash) ارسال می‌گردد. گلیف‌های «odd-style» استفاده نمی‌شوند (آن‌ها فقط برای نشان دادن اینکه می‌توان چند مقدار را در نقشه تعریف کرد، اضافه شده‌اند).

```css
/* At-rule for "nice-style", "odd-style", and "swishy" in Font One */
@font-feature-values Font One {
  @styleset {
    nice-style: 12; /* name used to represent the alternate set of glyphs at index 12 */
    odd-style: 10; /* name used to represent the alternate set of glyphs at index 10 */
  }
  @swash {
    swishy: 1; /* name used to represent the alternate set of glyphs at index 1 */
  }
}

/* Apply the at-rules to the appropriate selectors */
.nice-look {
  font-variant-alternates: styleset(nice-style);
}
.swoosh {
  font-variant-alternates: swash(swishy);
}
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 100px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### JavaScript

کد زیر، `CSSFontFeatureValuesRule` متناظر با اتریول (at-rule) CSS یعنی `@font-feature-values` را که در بالا اضافه شد، پیدا می‌کند. سپس مقادیر ویژگی‌های `styleset` و `swash` را که توسط نمونه‌های `CSSFontFeatureValuesMap` نمایش داده می‌شوند، با استفاده از متد [`forEach()`](/en-US/docs/Web/API/CSSFontFeatureValuesMap/forEach) پیمایش می‌کند. در هر مرحله، نام‌های تعریف‌شده توسط کاربر و مقادیر ایندکس را ثبت می‌کند.

```js
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const rules = document.querySelector("#css-output").sheet.cssRules;
const fontOne = rules[0]; // A CSSFontFeatureValuesRule
if (fontOne.styleset) {
  // styleset property is supported
  log(
    "The user has defined the following name(s)/index(s) for CSSFontFeatureValuesRule.styleset:",
  );
  fontOne.styleset.forEach((value, key) => log(` ${key} : ${value}`));
} else {
  log("Browser does not support CSSFontFeatureValuesMap.styleset property.");
}

if (fontOne.swash) {
  log(
    "The user has defined the following name(s)/index(s) for CSSFontFeatureValuesRule.swash:",
  );
  fontOne.swash.forEach((value, key) => log(` ${key} : ${value}`));
} else {
  log("Browser does not support CSSFontFeatureValuesMap.swash property.");
}
```

#### نتیجه

{{EmbedLiveSample("Logging user-defined names", "100%", "200px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("@font-feature-values")}}