```markdown
---
title: "CSSMathNegate: CSSMathNegate() constructor"
short-title: CSSMathNegate()
slug: Web/API/CSSMathNegate/CSSMathNegate
page-type: web-api-constructor
browser-compat: api.CSSMathNegate.CSSMathNegate
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازندهٔ **`CSSMathNegate()`** یک شیء جدید از نوع {{domxref("CSSMathNegate")}} می‌سازد که مقدار داده‌شده به آن را منفی می‌کند.

## نحو

```js-nolint
new CSSMathNegate(arg)
```

### پارامترها

- `arg`
  - : یک عدد یا {{domxref("CSSNumericValue")}} که مقداری را که باید منفی شود نشان می‌دهد.

### استثناها

هیچ‌کدام.

## مثال‌ها

### استفادهٔ پایه

کد زیر یک شیء `CSSMathNegate` از یک طول می‌سازد و سپس نام سازنده، `value` و رشته‌سازی شیء (از طریق {{domxref("CSSStyleValue/toString","toString()")}}) را در کنسول ثبت می‌کند.

```js
const negated = new CSSMathNegate(CSS.px(10));

console.log(negated.constructor.name); // "CSSMathNegate"
console.log(negated.value); // CSSUnitValue {value: 10, unit: "px"}
console.log(negated.toString()); // "calc(-10px)"
```

توجه کنید که اگر یک عدد ساده به `arg` داده شود، `value` به یک {{domxref("CSSUnitValue")}} با واحد `"number"` تبدیل می‌شود:

```js
const negatedNumber = new CSSMathNegate(4);

console.log(negatedNumber.value); // CSSUnitValue {value: 4, unit: "number"}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```