---
title: "CSSNumericValue: mul() method"
short-title: mul()
slug: Web/API/CSSNumericValue/mul
page-type: web-api-instance-method
browser-compat: api.CSSNumericValue.mul
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`mul()`** در رابط {{domxref("CSSNumericValue")}} مقدار `CSSNumericValue` را در مقادیر داده‌شده ضرب می‌کند.

## Syntax

```js-nolint
mul()
mul(number1)
mul(number1, number2)
mul(number1, number2, /* …, */ numberN)
```

### Parameters

- `number1`, …, `numberN` {{optional_inline}}
  - : یا یک عدد است یا یک {{domxref('CSSNumericValue')}}.

### Return value

یک {{domxref('CSSMathProduct')}}، یا اگر `this` و همهٔ آرگومان‌ها اعداد ساده باشند، یا همه به جز یکی از آن‌ها اعداد ساده باشند، یک {{domxref('CSSUnitValue')}}.

### Exceptions

- {{jsxref("TypeError")}}
  - : اگر نوع نامعتبری به متد传入 شود، پرتاب می‌شود.

## Examples

### Basic usage

```js
let mathProduct = CSS.px(23).mul(CSS.percent(4)).mul(CSS.cm(3)).mul(CSS.in(9));
// Prints "calc(23px * 4% * 3cm * 9in)"
console.log(mathProduct.toString());
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}