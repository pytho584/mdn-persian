---
title: "CSSMathClamp: CSSMathClamp() constructor"
short-title: CSSMathClamp()
slug: Web/API/CSSMathClamp/CSSMathClamp
page-type: web-api-constructor
browser-compat: api.CSSMathClamp.CSSMathClamp
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازنده **`CSSMathClamp()`** یک شیء جدید از نوع {{domxref("CSSMathClamp")) می‌سازد که تابع `clamp()` در CSS را نمایش می‌دهد.

## Syntax (نحو)

```js-nolint
new CSSMathClamp(lower, value, upper)
```

### پارامترها

- `lower`
  - : یک عدد یا {{domxref("CSSNumericValue")}} که حداقل مقدار را مشخص می‌کند.
- `value`
  - : یک عدد یا {{domxref("CSSNumericValue")}} که مقدار ترجیحی را مشخص می‌کند.
- `upper`
  - : یک عدد یا {{domxref("CSSNumericValue")}} که حداکثر مقدار را مشخص می‌کند.

### استثناها

- [`TypeError`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError)
  - : در صورتی که پارامترها دارای واحدهای ناسازگار باشند، پرتاب می‌شود. به عنوان مثال، ترکیب یک مقدار طول با یک مقدار زمان.

## مثال‌ها

### استفاده پایه

کد زیر یک نمونه از `CSSMathClamp` از سه طول می‌سازد و سپس ویژگی‌های `lower`، `value` و `upper` آن را بازخوانی می‌کند.

```js
const clamp = new CSSMathClamp(CSS.px(10), CSS.percent(50), CSS.px(500));

console.log(clamp.constructor.name); // "CSSMathClamp"
console.log(clamp.lower); // CSSUnitValue {value: 10, unit: "px"}
console.log(clamp.value); // CSSUnitValue {value: 50, unit: "percent"}
console.log(clamp.upper); // CSSUnitValue {value: 500, unit: "px"}
```

### مدیریت نوع‌های ناسازگار

سازنده در صورتی که سه آرگومان به یک نوع سازگار تبدیل نشوند، یک `TypeError` پرتاب می‌کند. در کد زیر یک طول را با یک زمان ترکیب کرده و خطا را ثبت می‌کنیم.

```js
try {
  // ترکیب طول (px) با زمان (s): انواع ناسازگار
  new CSSMathClamp(CSS.px(10), CSS.s(2), CSS.px(500));
} catch (e) {
  console.log(e instanceof TypeError); // true
  console.log(e.message);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}