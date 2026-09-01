---
title: "CSSNumericValue: div() method"
short-title: div()
slug: Web/API/CSSNumericValue/div
page-type: web-api-instance-method
browser-compat: api.CSSNumericValue.div
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`div()`** از رابط {{domxref("CSSNumericValue")}}، مقدار `CSSNumericValue` را بر مقدار داده‌شده تقسیم می‌کند.

## نحو

```js-nolint
div()
div(number1)
div(number1, number2)
div(number1, number2, /* …, */ numberN)
```

### پارامترها

- `number1`، …، `numberN` {{optional_inline}}
  - : یا یک عدد یا یک {{domxref('CSSNumericValue')}}.

### مقدار بازگشتی

یک {{domxref('CSSMathProduct')}}، یا یک {{domxref('CSSUnitValue')}} اگر `this` و همه آرگومان‌ها اعداد ساده باشند، یا همه به‌جز یکی از آن‌ها.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر نوع نامعتبری به متد ارسال شده باشد پرتاب می‌شود.
- [`RangeError`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/RangeError)
  - : اگر هر یک از `number1`، …، `numberN` برابر با 0 یا 0- باشد (یا به آن‌ها تبدیل شود) پرتاب می‌شود.

## مثال‌ها

### استفاده پایه

```js
let mathProduct = CSS.px(24).div(CSS.percent(4));
// چاپ می‌کند "calc(24px / 4%)"
mathProduct.toString();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}