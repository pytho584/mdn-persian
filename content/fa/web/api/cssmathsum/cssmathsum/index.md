---
title: "CSSMathSum: CSSMathSum() constructor"
short-title: CSSMathSum()
slug: Web/API/CSSMathSum/CSSMathSum
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.CSSMathSum.CSSMathSum
---

{{APIRef("CSS Typed Object Model API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

سازندهٔ **`CSSMathSum()`** یک شیء جدید {{domxref("CSSMathSum")}} می‌سازد که مجموع آرگومان‌های ارسال‌شده به آن را نشان می‌دهد.

آرگومان‌های عددی در شیءهای {{domxref("CSSUnitValue")}} با واحد `"number"` قرار می‌گیرند.
همهٔ آرگومان‌ها به عنوان موارد جداگانه در ویژگی {{domxref("CSSMathSum/values","values")}} آن ذخیره می‌شوند.

## نحو

```js-nolint
new CSSMathSum(arg1)
new CSSMathSum(arg1, arg2)
new CSSMathSum(arg1, arg2, /* …, */ argN)
```

### پارامترها

- `arg1`، …، `argN`
  - : یک یا چند عدد یا شیء {{domxref("CSSNumericValue")}}.

### استثناها

- `SyntaxError` {{domxref("DOMException")}}
  - : اگر هیچ آرگومانی ارسال نشود پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر نوع‌های `arg1`، …، `argN` ناسازگار باشند پرتاب می‌شود.

## مثال‌ها

### استفادهٔ پایه

کد زیر یک نمونهٔ `CSSMathSum` از سه مقدار می‌سازد و سپس ویژگی‌های `operator` و `values` آن را می‌خواند.

```js
const sum = new CSSMathSum(CSS.px(10), CSS.em(5), CSS.percent(50));

console.log(sum.constructor.name); // "CSSMathSum"
console.log(sum.operator); // 'sum'
console.log(sum.values); // CSSNumericArray {0: CSSUnitValue, 1: CSSUnitValue, 2: CSSUnitValue, length: 3}
console.log(sum.values[0]); // CSSUnitValue {value: 10, unit: "px"}
```

### آرگومان‌های خالی

اگر سازنده بدون آرگومان فراخوانی شود، یک `SyntaxError` پرتاب می‌کند.

```js
try {
  new CSSMathSum();
} catch (e) {
  console.log(e instanceof DOMException); // true
  console.log(e.name); // "SyntaxError"
}
```

### مدیریت نوع‌های ناسازگار

اگر مقدارها به یک نوع سازگار تبدیل نشوند، سازنده یک `TypeError` پرتاب می‌کند.
در کد زیر یک طول را با یک زمان ترکیب می‌کنیم و خطا را ثبت می‌کنیم.

```js
try {
  // طول (px) را با زمان (s) ترکیب می‌کند: نوع‌های ناسازگار
  new CSSMathSum(CSS.px(10), CSS.s(2));
} catch (e) {
  console.log(e instanceof TypeError); // true
  console.log(e.message);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
