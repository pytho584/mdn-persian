---
title: "CSSNumericValue: sub() method"
short-title: sub()
slug: Web/API/CSSNumericValue/sub
page-type: web-api-instance-method
browser-compat: api.CSSNumericValue.sub
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`sub()`** از رابط {{domxref("CSSNumericValue")}} یک عدد داده‌شده را از `CSSNumericValue` کم می‌کند.

## Syntax

```js-nolint
sub()
sub(number1)
sub(number1, number2)
sub(number1, number2, /* …, */ numberN)
```

### Parameters

- `number1`، …، `numberN` {{optional_inline}}
  - : یا یک عدد یا یک {{domxref('CSSNumericValue')}}.

### Return value

یک {{domxref('CSSMathSum')}}، یا اگر `this` و همه آرگومان‌ها واحد مشترکی داشته باشند یک {{domxref('CSSUnitValue')}}.

### Exceptions

- {{jsxref("TypeError")}}
  - : اگر نوع نامعتبری به متد ارسال شود پرتاب می‌شود.

## Examples

### Basic usage

```js
let mathSum = CSS.px(23).sub(CSS.percent(4)).sub(CSS.cm(3)).sub(CSS.in(9));
// Prints "calc(23px - 4% - 3cm - 9in)"
console.log(mathSum.toString());
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
