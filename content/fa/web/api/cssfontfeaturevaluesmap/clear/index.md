---
title: "CSSFontFeatureValuesMap: clear() method"
short-title: clear()
slug: Web/API/CSSFontFeatureValuesMap/clear
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesMap.clear
---

{{APIRef("CSSOM")}}{{SeeCompatTable}}

متد **`clear()`** از واسط {{domxref("CSSFontFeatureValuesMap")}} تمام اعلان‌های موجود در `CSSFontFeatureValuesMap` را حذف می‌کند.

## نحو (Syntax)

```js-nolint
clear()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

هیچکدام ({{jsxref("undefined")}}).

## مثال‌ها

### استفاده پایه

مثال زیر تمام اعلان‌های موجود در بلوک ویژگی [`@swash`](/en-US/docs/Web/CSS/Reference/At-rules/@font-feature-values#swash) را حذف می‌کند. این مثال از `@swash` استفاده می‌کند اما با سایر [بلوک‌های مقادیر ویژگی](/en-US/docs/Web/CSS/Reference/At-rules/@font-feature-values#feature_value_blocks) نیز کار می‌کند.

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
// دریافت قوانین
const myRule = document.styleSheets[0].cssRules[0];
console.log(myRule.swash.size); // چاپ می‌کند 2
myRule.swash.clear();
console.log(myRule.swash.size); // چاپ می‌کند 0
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Map.prototype.clear()](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/clear)