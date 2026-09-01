---
title: "CSSMathInvert: CSSMathInvert() constructor"
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازنده‌ی **`CSSMathInvert()`** یک شیء جدید از {{domxref("CSSMathInvert")}} می‌سازد که معکوس (وارون) یک {{domxref('CSSNumericValue')}} را نمایش می‌دهد.

## Syntax

```js-nolint
new CSSMathInvert(arg)
```

### Parameters

- `arg`
  - : یک عدد یا {{domxref('CSSNumericValue')}} که مقدار مورد نظر برای معکوس‌سازی را نمایش می‌دهد.

### Exceptions

هیچکدام.

## Examples

### استفاده پایه

کد زیر یک شیء `CSSMathInvert` از یک درصد می‌سازد، سپس نام سازنده، `value` و رشته‌سازی شیء (از {{domxref("CSSStyleValue/toString","toString()")}}) را لاگ می‌کند.

```js
const inverted = new CSSMathInvert(CSS.percent(4));

console.log(inverted.constructor.name); // "CSSMathInvert"
console.log(inverted.value); // CSSUnitValue {value: 4, unit: "percent"}
console.log(inverted.toString()); // "calc(1 / 4%)"
```

توجه کنید که اگر یک عدد ساده به `arg` داده شود، `value` به یک {{domxref("CSSUnitValue")}} با واحد `"number"` تبدیل می‌شود:

```js
const invertedNumber = new CSSMathInvert(4);

console.log(invertedNumber.value); // CSSUnitValue {value: 4, unit: "number"}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}