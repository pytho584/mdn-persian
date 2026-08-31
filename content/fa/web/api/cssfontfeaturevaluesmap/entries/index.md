---
title: "CSSFontFeatureValuesMap: entries() method"
short-title: entries()
slug: Web/API/CSSFontFeatureValuesMap/entries
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesMap.entries
---

{{APIRef("CSSOM")}}{{SeeCompatTable}}

متد **`entries()`** از نمونه‌های {{domxref("CSSFontFeatureValuesMap")}} یک شیء جدید از نوع [تکرارگر نقشه](/en-US/docs/Web/API/CSSFontFeatureValuesMap/Symbol.iterator) برمی‌گرداند که شامل جفت‌های `[key, value]` برای هر اعلان در این `CSSFontFeatureValuesMap` به ترتیب درج است.

## نحو

```js-nolint
entries()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک [شیء تکرارگر](/en-US/docs/Web/API/CSSFontFeatureValuesMap/Symbol.iterator) جدید و قابل تکرار.

## مثال‌ها

### استفاده پایه

مثال زیر ورودی‌ها را به متغیر `swashes` اختصاص می‌دهد و سپس دو مقدار اول را ثبت می‌کند. این مثال از `@swash` استفاده می‌کند، اما با سایر [بلوک‌های مقدار ویژگی](/en-US/docs/Web/CSS/Reference/At-rules/@font-feature-values#feature_value_blocks) نیز کار می‌کند.

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
// دریافت ورودی‌های swash
const swashes = myRule.swash.entries();
console.log(swashes.next().value); // ["swishy", [1]] را ثبت می‌کند
console.log(swashes.next().value); // ["swashy", [2]] را ثبت می‌کند
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Map.prototype.entries()](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/entries)