---
title: "CSSFontFeatureValuesMap: forEach() method"
short-title: forEach()
slug: Web/API/CSSFontFeatureValuesMap/forEach
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesMap.forEach
---

{{APIRef("CSSOM")}}{{SeeCompatTable}}

متد **`forEach()`** در نمونه‌های {{domxref("CSSFontFeatureValuesMap")}} یک تابع ارائه‌شده را برای هر جفت کلید/مقدار در این نقشه، به ترتیب درج، اجرا می‌کند.

## نحو (Syntax)

```js-nolint
forEach(callbackFn)
forEach(callbackFn, thisArg)
```

### پارامترها

- `callbackFn`
  - : تابعی که برای هر ورودی در نقشه اجرا می‌شود. این تابع با آرگومان‌های زیر فراخوانی می‌شود:
    - `value`
      - : مقدار هر تکرار.
    - `key`
      - : کلید هر تکرار.
    - `map`
      - : نقشه‌ای که در حال پیمایش است.
- `thisArg` {{optional_inline}}
  - : مقداری که به عنوان `this` هنگام اجرای `callbackFn` استفاده می‌شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

### استفاده پایه

مثال زیر `key` و `value` را برای هر ورودی در قانون `@swash` ثبت می‌کند. این مثال از `@swash` استفاده می‌کند، اما با سایر [بلوک‌های مقادیر ویژگی‌ها](/en-US/docs/Web/CSS/Reference/At-rules/@font-feature-values#feature_value_blocks) نیز کار می‌کند.

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
// تابعی که به عنوان callback استفاده می‌شود
function logSwashes(value, key, map) {
  console.log(`('${key}') = ${value}`);
}
// دریافت قوانین
const myRule = document.styleSheets[0].cssRules[0];
myRule.swash.forEach(logSwashes);
// خروجی:
// "('swishy') = 1"
// "('swashy') = 2"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Map.prototype.forEach()](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/forEach)