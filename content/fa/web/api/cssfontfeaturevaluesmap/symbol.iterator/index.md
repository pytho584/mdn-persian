---
title: "CSSFontFeatureValuesMap: [Symbol.iterator]() method"
short-title: "[Symbol.iterator]()"
slug: Web/API/CSSFontFeatureValuesMap/Symbol.iterator
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesMap.@@iterator
---

{{APIRef("CSSOM")}}{{SeeCompatTable}}

متد **`[Symbol.iterator]()`** از رابط {{domxref("CSSFontFeatureValuesMap")}} پروتکل [iterable protocol](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols) را پیاده‌سازی می‌کند و به iteratorهای داخلی اجازه می‌دهد که توسط بیشتر نحوهایی که منتظر iterable هستند، مانند [spread syntax](/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) و حلقه‌های {{jsxref("Statements/for...of", "for...of")}} مصرف شوند. این متد مقدار [`this`](/en-US/docs/Web/JavaScript/Reference/Operators/this) را برمی‌گرداند که خود شیء iterator است.

## نحو (Syntax)

```js-nolint
iterator[Symbol.iterator]()
```

### پارامترها

هیچ.

### مقدار برگشتی

مقدار [`this`](/en-US/docs/Web/JavaScript/Reference/Operators/this) که خود شیء iterator است.

## مثال‌ها

### استفاده پایه

مثال زیر از iterator داخلی `CSSFontFeatureValuesMap` برای ثبت مقادیر با استفاده از حلقه `for...of` استفاده می‌کند. این مثال از `@swash` استفاده می‌کند اما با سایر [feature value blocks](/en-US/docs/Web/CSS/Reference/At-rules/@font-feature-values#feature_value_blocks) نیز کار می‌کند.

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
// get the rules
const myRule = document.styleSheets[0].cssRules[0];
for (const value of myRule.swash.keys()) {
  console.log(value);
}
// Logs: "swishy", "swashy"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [`Iterator.prototype[Symbol.iterator]()`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Iterator/Symbol.iterator)
- {{jsxref("Iterator")}}