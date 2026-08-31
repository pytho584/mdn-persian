---
title: "CSSFontFeatureValuesMap: get() method"
short-title: get()
slug: Web/API/CSSFontFeatureValuesMap/get
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesMap.get
---

{{APIRef("CSSOM")}}{{SeeCompatTable}}

متد **`get()`** در رابط {{domxref("CSSFontFeatureValuesMap")}} مقداری را برمی‌گرداند که با کلید داده‌شده در این `CSSFontFeatureValuesMap` مطابقت دارد؛ یا اگر کلیدی وجود نداشته باشد، `undefined` را برمی‌گرداند.

## Syntax

```js-nolint
get(property)
```

### Parameters

- `key`
  - : کلیدی که مقدار مربوط به آن باید از شیء `CSSFontFeatureValuesMap` بازگردانده شود.

### Return value

اگر یک ورودی با کلید مشخص‌شده در شیء `CSSFontFeatureValuesMap` وجود داشته باشد، `true` برمی‌گرداند؛ در غیر این صورت `false`.

## Examples

### Basic usage

مثال زیر مقادیری را که با `key`ها در قانون `@swash` مطابقت دارند دریافت می‌کند. این مثال از `@swash` استفاده می‌کند اما با سایر [بلوک‌های مقدار ویژگی](/en-US/docs/Web/CSS/Reference/At-rules/@font-feature-values#feature_value_blocks) نیز کار می‌کند.

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
console.log(myRule.swash.get("swishy")); // logs [1]
console.log(myRule.swash.get("swashy")); // logs [2]
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Map.prototype.get()](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/get)