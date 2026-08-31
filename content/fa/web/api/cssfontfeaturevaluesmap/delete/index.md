---
title: "CSSFontFeatureValuesMap: delete() method"
---

---
title: "CSSFontFeatureValuesMap: delete() method"
short-title: delete()
slug: Web/API/CSSFontFeatureValuesMap/delete
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesMap.delete
---

{{APIRef("CSSOM")}}{{SeeCompatTable}}

متد **`delete()`** از رابط {{domxref("CSSFontFeatureValuesMap")}} اعلامیه‌ی CSS مربوط به ویژگی داده‌شده را در `CSSFontFeatureValuesMap` حذف می‌کند.

## Syntax

```js-nolint
delete(property)
```

### پارامترها

- `property`
  - : یک شناسه که نشان‌دهنده‌ی اعلامیه‌ای است که باید حذف شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

### استفاده‌ی پایه

مثال زیر اولین اعلامیه را درون بلوک ویژگی [`@swash`](/en-US/docs/Web/CSS/Reference/At-rules/@font-feature-values#swash) حذف می‌کند. این مثال از `@swash` استفاده می‌کند اما با سایر [بلوک‌های مقادیر ویژگی](/en-US/docs/Web/CSS/Reference/At-rules/@font-feature-values#feature_value_blocks) نیز کار می‌کند.

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
console.log(myRule.swash.has("swishy")); // logs true
myRule.swash.delete("swishy");
console.log(myRule.swash.has("swishy")); // logs false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Map.prototype.delete()](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/delete)