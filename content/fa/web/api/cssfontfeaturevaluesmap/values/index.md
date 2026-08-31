---
title: "CSSFontFeatureValuesMap: values() method"
short-title: values()
slug: Web/API/CSSFontFeatureValuesMap/values
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesMap.values
---

{{APIRef("CSSOM")}}{{SeeCompatTable}}

متد **`values()`** از نمونه‌های {{domxref("CSSFontFeatureValuesMap")}} یک [تکرارگر نقشه](/en-US/docs/Web/API/CSSFontFeatureValuesMap/Symbol.iterator) جدید برمی‌گرداند که شامل جفت‌های `[key, value]` برای هر اعلان در این `CSSFontFeatureValuesMap` به ترتیب درج است.

## Syntax

```js-nolint
values()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک [شیء تکرارگر](/en-US/docs/Web/API/CSSFontFeatureValuesMap/Symbol.iterator) جدید و قابل تکرار.

## مثال‌ها

### استفاده پایه

مثال زیر مقادیر را به متغیر `swashValues` اختصاص می‌دهد و سپس دو مقدار اول را ثبت می‌کند. این مثال از `@swash` استفاده می‌کند اما با سایر [بلوک‌های مقدار ویژگی](/en-US/docs/Web/CSS/Reference/At-rules/@font-feature-values#feature_value_blocks) نیز کار می‌کند.

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
// دریافت مقادیر swash
const swashValues = myRule.swash.values();
console.log(swashValues.next().value); // [1] را ثبت می‌کند
console.log(swashValues.next().value); // [2] را ثبت می‌کند
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Map.prototype.values()](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/values)