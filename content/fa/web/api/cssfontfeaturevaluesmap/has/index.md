---
title: "CSSFontFeatureValuesMap: has() method"
short-title: has()
slug: Web/API/CSSFontFeatureValuesMap/has
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesMap.has
---

{{APIRef("CSSOM")}}{{SeeCompatTable}}

متد **`has()`** از رابط {{domxref("CSSFontFeatureValuesMap")}} یک مقدار بولی بازمی‌گرداند که نشان می‌دهد آیا یک ورودی با کلید مشخص‌شده در این `CSSFontFeatureValuesMap` وجود دارد یا خیر.

## Syntax

```js-nolint
has(property)
```

### پارامترها

- `key`
  - : کلید مقداری که باید از شیء `CSSFontFeatureValuesMap` بازگردانده شود.

### مقدار بازگشتی

مقدار مرتبط با کلید مشخص‌شده در شیء `CSSFontFeatureValuesMap`. اگر کلید پیدا نشود، [undefined](/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined) بازگردانده می‌شود.

## مثال‌ها

### استفاده پایه

مثال زیر `true` یا `false` را برمی‌گرداند اگر قاعده `@swash` حاوی `key` باشد. این مثال از `@swash` استفاده می‌کند اما با سایر [بلوک‌های مقادیر ویژگی](/en-US/docs/Web/CSS/Reference/At-rules/@font-feature-values#feature_value_blocks) نیز کار می‌کند.

#### CSS

```css
@font-feature-values "MonteCarlo" {
  @swash {
    swishy: 1;
    swashy: 2;
  }
}
```

#### JavaScript

```js
// دریافت قواعد
const myRule = document.styleSheets[0].cssRules[0];
console.log(myRule.swash.has("swishy")); // true را ثبت می‌کند
console.log(myRule.swash.has("swooshy")); // false را ثبت می‌کند
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Map.prototype.has()](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/has)