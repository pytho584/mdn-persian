---
title: "CSSMathMin: CSSMathMin() constructor"
short-title: CSSMathMin()
slug: Web/API/CSSMathMin/CSSMathMin
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.CSSMathMin.CSSMathMin
---

{{SeeCompatTable}}{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازنده‌ی **`CSSMathMin()`** یک شیء جدید از نوع {{domxref("CSSMathMin")}} می‌سازد که تابع CSS {{CSSXref('min','min()')}} را نمایش می‌دهد.

## نحو (Syntax)

```js-nolint
new CSSMathMin(arg1)
new CSSMathMin(arg1, arg2)
new CSSMathMin(arg1, arg2, /* …, */ argN)
```

### پارامترها

- `arg1`، …, `argN`
  - : فهرستی از اعداد یا اشیاء {{domxref("CSSNumericValue")}}.

### استثناها (Exceptions)

- `SyntaxError` {{domxref("DOMException")}}
  - : اگر هیچ آرگومانی ارسال نشود، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر نوع `arg1`، …, `argN` ناسازگار باشد (مثلاً ترکیب یک {{cssxref('length')}} با یک {{cssxref('angle')}})، طوری که نوع مشترکی برای مقایسه قابل تعیین نباشد، پرتاب می‌شود.

## مثال‌ها

### استفاده‌ی پایه

کد زیر یک نمونه `CSSMathMin` از سه مقدار می‌سازد و سپس ویژگی‌های `operator` و `values` آن را بازخوانی می‌کند.

```js
const min = new CSSMathMin(CSS.px(10), CSS.em(5), CSS.percent(50));

console.log(min.constructor.name); // "CSSMathMin"
console.log(min.operator); // 'min'
console.log(min.values); // CSSNumericArray {0: CSSUnitValue, 1: CSSUnitValue, 2: CSSUnitValue, length: 3}
console.log(min.values[0]); // CSSUnitValue {value: 10, unit: "px"}
```

### مدیریت نوع‌های ناسازگار

اگر مقادیر به یک نوع سازگار قابل تبدیل نباشند، سازنده یک `TypeError` پرتاب می‌کند.
در کد زیر یک طول (length) را با یک زمان (time) ترکیب می‌کنیم و خطا را در خروجی ثبت می‌کنیم.

```js
try {
  // ترکیب یک طول (px) با یک زمان (s): نوع‌های ناسازگار
  new CSSMathMin(CSS.px(10), CSS.s(2));
} catch (e) {
  console.log(e instanceof TypeError); // true
  console.log(e.message);
}
```

### آرگومان‌های خالی

اگر سازنده بدون هیچ آرگومانی فراخوانی شود، یک `SyntaxError` پرتاب می‌کند.

```js
try {
  new CSSMathMin();
} catch (e) {
  console.log(e instanceof DOMException); // true
  console.log(e.name); // "SyntaxError"
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}