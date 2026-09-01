---
title: "CSSNumericValue: max() method"
short-title: max()
slug: Web/API/CSSNumericValue/max
page-type: web-api-instance-method
browser-compat: api.CSSNumericValue.max
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`max()`** در رابط {{domxref("CSSNumericValue")}}، بزرگترین مقدار را از میان مقادیر ارسال‌شده برمی‌گرداند.
مقادیر ارسال‌شده باید از نوع یکسانی باشند.

## نحو (Syntax)

```js-nolint
max()
max(number1)
max(number1, number2)
max(number1, number2, /* …, */ numberN)
```

### پارامترها

- `number1`، …، `numberN` {{optional_inline}}
  - : یا یک عدد است یا یک {{domxref('CSSNumericValue')}}.

### مقدار بازگشتی

یک {{domxref('CSSUnitValue')}}.

### استثناها

- {{jsxref("TypeError")}}
  - : زمانی پرتاب می‌شود که یک نوع نامعتبر به متد ارسال شده باشد.

## مثال‌ها

### استفاده پایه

همانطور که قبلاً گفته شد، همه مقادیر ارسال‌شده باید از نوع و مقدار یکسانی باشند.
برخی از مثال‌های زیر نشان می‌دهند که وقتی اینطور نباشند چه اتفاقی می‌افتد.

```js
// چاپ می‌کند "2cm"
console.log(CSS.cm("1").max(CSS.cm("2")).toString());

// چاپ می‌کند "max(1cm, 0.393701in)"
console.log(CSS.cm("1").max(CSS.in("0.393701")).toString());
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}