---
title: "CSSMathProduct: CSSMathProduct() constructor"
short-title: CSSMathProduct()
slug: Web/API/CSSMathProduct/CSSMathProduct
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.CSSMathProduct.CSSMathProduct
---

{{APIRef("CSS Typed Object Model API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

سازندهٔ **`CSSMathProduct()`** یک شیء جدید از نوع {{domxref("CSSMathProduct")}} می‌سازد که حاصلضرب آرگومان‌های ارسال‌شده به آن را نشان می‌دهد.

آرگومان‌های عددی در اشیاء {{domxref("CSSUnitValue")}} با واحد `"number"` قرار می‌گیرند. همهٔ آرگومان‌ها به‌صورت آیتم‌های جداگانه در ویژگی {{domxref("CSSMathProduct/values","values")}} ذخیره می‌شوند.

## سینتکس

```js-nolint
new CSSMathProduct(arg1)
new CSSMathProduct(arg1, arg2)
new CSSMathProduct(arg1, arg2, /* …, */ argN)
```

### پارامترها

- `arg1`, …, `argN`
  - : یک یا چند عدد یا شیء {{domxref("CSSNumericValue")}}.

### استثناها

- `SyntaxError` {{domxref("DOMException")}}
  - : اگر هیچ آرگومانی ارسال نشود، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر نوع‌های `arg1`, …, `argN` نتوانند در یک حاصلضرب ترکیب شوند، پرتاب می‌شود. این مورد نادر است؛ ضرب کردن مقادیر با واحدهای مختلف (برای مثال طول در زمان) مجاز است و یک نوع مرکب ایجاد می‌کند.

## مثال‌ها

### کاربرد پایه

کد زیر یک نمونهٔ `CSSMathProduct` از دو مقدار می‌سازد و سپس ویژگی‌های `operator` و `values` آن را می‌خواند.

```js
const product = new CSSMathProduct(CSS.px(10), CSS.percent(50));

console.log(product.constructor.name); // "CSSMathProduct"
console.log(product.operator); // 'product'
console.log(product.values); // CSSNumericArray {0: CSSUnitValue, 1: CSSUnitValue, length: 2}
console.log(product.values[0]); // CSSUnitValue {value: 10, unit: "px"}
```

### آرگومان‌های خالی

اگر سازنده با هیچ آرگومانی فراخوانده شود، یک `SyntaxError` پرتاب می‌کند.

```js
try {
  new CSSMathProduct();
} catch (e) {
  console.log(e instanceof DOMException); // true
  console.log(e.name); // "SyntaxError"
}
```

### مدیریت درصدهای ناسازگار

ضرب کردن طول در زمان، یک نوع مرکب معتبر (هرچند غیرمعمول) تولید می‌کند — برخلاف جمع، ضرب نیازی ندارد که آرگومان‌هایش در یک بُعد مشترک باشند.

```js
const compound = new CSSMathProduct(CSS.px(10), CSS.s(2));

console.log(compound.constructor.name); // "CSSMathProduct"
console.log(compound.toString()); // "calc(10px * 2s)"
```

یک `TypeError` ممکن است در حالت پیچیده‌تری رخ دهد که در آن دو یا چند آرگومان خودشان مقادیر ترکیبی باشند که هر کدام یک درصد را با یک واحد متفاوت ترکیب می‌کنند و حاصلضرب نمی‌تواند آن‌ها را به یک نوع سازگار تفکیک کند.

در کد زیر، `percentageLength` یک درصد را با طول ترکیب می‌کند (بنابراین درصد آن به `"length"` تفکیک می‌شود) و `percentageAngle` یک درصد را با زاویه ترکیب می‌کند (بنابراین درصد آن به `"angle"` تفکیک می‌شود). ضرب آن‌ها ناموفق است، زیرا درصدهای آن‌ها به یک نوع مشترک قابل تفکیک نیستند.

```js
const percentageLength = CSS.percent(50).add(CSS.px(10)); // percentage resolves to "length"
const percentageAngle = CSS.percent(50).add(CSS.deg(10)); // percentage resolves to "angle"

try {
  new CSSMathProduct(percentageLength, percentageAngle);
} catch (e) {
  console.log(e instanceof TypeError); // true
  console.log(e.message);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}