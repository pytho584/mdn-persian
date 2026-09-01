---
title: "CSSNumericValue: add() method"
short-title: add()
slug: Web/API/CSSNumericValue/add
page-type: web-api-instance-method
browser-compat: api.CSSNumericValue.add
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`add()`** از رابط {{domxref("CSSNumericValue")}} یک عدد داده شده را به `CSSNumericValue` اضافه می‌کند.

## نحو

```js-nolint
add()
add(number1)
add(number1, number2)
add(number1, number2, /* …, */ numberN)
```

### پارامترها

- `number1`، …، `numberN` {{optional_inline}}
  - : یک عدد یا یک {{domxref('CSSNumericValue')}}.

### مقدار برگشتی

یک {{domxref('CSSMathSum')}}، یا یک {{domxref('CSSUnitValue')}} اگر `this` و همه آرگومان‌ها واحد یکسانی داشته باشند.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر نوع نامعتبری به متد ارسال شود، پرتاب می‌شود.

## مثال‌ها

### استفاده پایه

```js
let mathSum = CSS.px(23).add(CSS.percent(4)).add(CSS.cm(3)).add(CSS.in(9));
// چاپ می‌کند "calc(23px + 4% + 3cm + 9in)"
console.log(mathSum.toString());
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}