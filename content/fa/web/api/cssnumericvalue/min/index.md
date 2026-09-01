---
title: "CSSNumericValue: min() method"
short-title: min()
slug: Web/API/CSSNumericValue/min
page-type: web-api-instance-method
browser-compat: api.CSSNumericValue.min
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`min()`** از رابط {{domxref("CSSNumericValue")}} کمترین مقدار را از میان مقادیری که به آن‌ها داده شده است برمی‌گرداند. مقادیر ارسال‌شده باید از نوع یکسانی باشند.

## نحو (Syntax)

```js-nolint
min()
min(number1)
min(number1, number2)
min(number1, number2, /* …, */ numberN)
```

### پارامترها

- `number1`، …، `numberN` {{optional_inline}}
  - : یک عدد یا یک {{domxref('CSSNumericValue')}}.

### مقدار بازگشتی

یک {{domxref('CSSUnitValue')}}.

### استثناها (Exceptions)

- {{jsxref("TypeError")}}
  - : اگر نوع نامعتبری به متد ارسال شده باشد، پرتاب می‌شود.

## مثال‌ها

### استفاده پایه

همانطور که قبلاً گفته شد، همه مقادیر ارسال‌شده باید از یک نوع و مقدار باشند. برخی از مثال‌های زیر نشان می‌دهند که وقتی اینطور نباشند چه اتفاقی می‌افتد.

```js
// چاپ می‌کند: "1cm"
console.log(CSS.cm("1").min(CSS.cm("2")).toString());

// چاپ می‌کند: "max(1cm, 0.393701in)"
console.log(CSS.cm("1").max(CSS.in("0.393701")).toString());
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}