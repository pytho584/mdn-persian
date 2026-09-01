---
title: "CSSNumericValue: equals() method"
short-title: equals()
slug: Web/API/CSSNumericValue/equals
page-type: web-api-instance-method
browser-compat: api.CSSNumericValue.equals
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`equals()`** در رابط {{domxref("CSSNumericValue")}} یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا مقادیر ارسال‌شده دقیقاً برابر هستند یا خیر.
برای اینکه مقدار `true` برگردد، همهٔ مقادیر ارسال‌شده باید از نوع و مقدار یکسان باشند و به همان ترتیب باشند.
این امکان را می‌دهد که برابری ساختاری به سرعت بررسی شود.

## Syntax

```js-nolint
equals()
equals(number1)
equals(number1, number2)
equals(number1, number2, /* …, */ numberN)
```

### Parameters

- `number1`, …, `numberN` {{optional_inline}}
  - : یا یک عدد است یا یک {{domxref('CSSNumericValue')}}.

### Return value

یک مقدار بولی.

### Exceptions

هیچ‌کدام.

## Examples

### Basic usage

همانطور که پیش‌تر گفته شد، همهٔ مقادیر ارسال‌شده باید از نوع و مقدار یکسان باشند و به همان ترتیب باشند.
برخی از مثال‌های زیر نشان می‌دهند که وقتی این شرایط برقرار نباشند چه اتفاقی می‌افتد.

```js
let cssMathSum = new CSSMathSum(CSS.px(1), CSS.px(2));
let matchingCssMathSum = new CSSMathSum(CSS.px(1), CSS.px(2));
// Prints true
console.log(cssMathSum.equals(matchingCssMathSum));

let otherCssMathSum = CSSMathSum(CSS.px(2), CSS.px(1));
// Prints false
console.log(cssMathSum.equals(otherCssMathSum));

// Also prints false
console.log(CSS.cm("1").equal(CSS.in("0.393701")));
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}