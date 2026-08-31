---
title: "CSSFontFeatureValuesMap: set() method"
short-title: set()
slug: Web/API/CSSFontFeatureValuesMap/set
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesMap.set
---

{{APIRef("CSSOM")}}{{SeeCompatTable}}

متد **`set()`** از نمونه‌های {{domxref("CSSFontFeatureValuesMap")}} یک ورودی جدید با کلید و مقدار مشخص به این `CSSFontFeatureValuesMap` اضافه می‌کند، یا اگر کلید از قبل وجود داشته باشد، ورودی موجود را به‌روزرسانی می‌کند.

## Syntax

```js-nolint
set(key, value)
```

### Parameters

- `key`
  - : کلید ورودی که باید به شیء `CSSFontFeatureValuesMap` اضافه یا در آن تغییر داده شود. می‌تواند هر مقداری باشد.
- `value`
  - : مقدار ورودی که باید به شیء `CSSFontFeatureValuesMap` اضافه یا در آن تغییر داده شود. باید یک عدد صحیح باشد که با `index` ویژگی جایگزین فونت مطابقت داشته باشد.

### Return value

شیء `CSSFontFeatureValuesMap`.

## Examples

### Basic usage

مثال زیر مقدار `swashy` را به‌روزرسانی می‌کند و یک اعلان سوم اضافه می‌کند. این مثال از `@swash` استفاده می‌کند اما با سایر [بلوک‌های مقدار ویژگی](/en-US/docs/Web/CSS/Reference/At-rules/@font-feature-values#feature_value_blocks) نیز کار می‌کند.

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
function logSwashes(value, key) {
  console.log(`('${key}') = ${value}`);
}
// get the rules
const myRule = document.styleSheets[0].cssRules[0];
// log current swashes
myRule.swash.forEach(logSwashes); // logs "('swishy') = 1", "('swashy') = 2"

// update swash with the key swashy
myRule.swash.set("swashy", 3);
myRule.swash.forEach(logSwashes); // logs "('swishy') = 1", "('swashy') = 3"

// add new swash with the key swooshy
myRule.swash.set("swooshy", 2);
myRule.swash.forEach(logSwashes); // logs "('swishy') = 1", "('swooshy') = 2", "('swashy') = 3"
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Map.prototype.set()](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/set)