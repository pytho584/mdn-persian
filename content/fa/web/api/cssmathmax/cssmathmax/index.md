---
title: "CSSMathMax: CSSMathMax() constructor"
short-title: CSSMathMax()
slug: Web/API/CSSMathMax/CSSMathMax
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.CSSMathMax.CSSMathMax
---

{{SeeCompatTable}}{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازندهٔ **`CSSMathMax()`** یک شیء جدید از نوع {{domxref("CSSMathMax")}} می‌سازد که تابع CSS {{CSSXref('max', 'max()')}} را نمایش می‌دهد.

## نحو (Syntax)

```js-nolint
new CSSMathMax(arg1)
new CSSMathMax(arg1, arg2)
new CSSMathMax(arg1, arg2, /* …, */ argN)
```

### پارامترها

- `arg1`، …، `argN`
  - : فهرستی از اعداد یا اشیاء {{domxref("CSSNumericValue")}}.

### استثناها (Exceptions)

- `SyntaxError` {{domxref("DOMException")}}
  - : اگر هیچ آرگومانی ارسال نشود، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر نوع `arg1`، …، `argN` ناسازگار باشد (مثلاً ترکیب یک {{cssxref('length')}} با یک {{cssxref('angle')}})، به‌گونه‌ای که نتوان نوع مشترکی برای مقایسه تعیین کرد، پرتاب می‌شود.

## مثال‌ها

### استفادهٔ پایه

کد زیر یک نمونه از `CSSMathMax` را از سه مقدار می‌سازد و سپس ویژگی‌های `operator` و `values` آن را بازخوانی می‌کند.

```js
const max = new CSSMathMax(CSS.px(10), CSS.em(5), CSS.percent(50));

console.log(max.constructor.name); // "CSSMathMax"
console.log(max.operator); // 'max'
console.log(max.values); // CSSNumericArray {0: CSSUnitValue, 1: CSSUnitValue, 2: CSSUnitValue, length: 3}
console.log(max.values[0]); // CSSUnitValue {value: 10, unit: "px"}
```

### مدیریت انواع ناسازگار

اگر مقادیر به نوع سازگاری تبدیل نشوند، سازنده یک `TypeError` پرتاب می‌کند.
در کد زیر یک طول را با یک زمان ترکیب می‌کنیم و خطا را ثبت می‌کنیم.

```js
try {
  // ترکیب یک طول (px) با یک زمان (s): انواع ناسازگار
  new CSSMathMax(CSS.px(10), CSS.s(2));
} catch (e) {
  console.log(e instanceof TypeError); // true
  console.log(e.message);
}
```

### آرگومان‌های خالی

اگر سازنده بدون آرگومان فراخوانی شود، یک `SyntaxError` پرتاب می‌کند.

```js
try {
  new CSSMathMax();
} catch (e) {
  console.log(e instanceof DOMException); // true
  console.log(e.name); // "SyntaxError"
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}