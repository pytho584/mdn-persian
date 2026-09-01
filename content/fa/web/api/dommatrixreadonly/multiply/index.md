---
title: "DOMMatrixReadOnly: multiply() method"
short-title: multiply()
slug: Web/API/DOMMatrixReadOnly/multiply
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.multiply
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`multiply()`** از رابط {{domxref("DOMMatrixReadOnly")}} یک ماتریس جدید ایجاد و بازمی‌گرداند که حاصل ضرب نقطه‌ای (dot product) ماتریس اصلی و پارامتر `otherMatrix` است. اگر `otherMatrix` حذف شود، ماتریس در ماتریسی ضرب می‌شود که تمام عناصر آن `0` هستند _به جز_ گوشه پایین-راست و عنصر بلافاصله بالای آن و سمت چپ آن: `m33` و `m34`. این مقادیر پیش‌فرض `1` دارند. ماتریس اصلی تغییر نمی‌کند.

برای تغییر ماتریس در حین ضرب، به {{domxref("DOMMatrix.multiplySelf()")}} مراجعه کنید.

## نحو (Syntax)

```js-nolint
multiply()
multiply(otherMatrix)
```

### پارامترها

- `otherMatrix` {{optional_inline}}
  - : ضرب‌کننده [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix).

### مقدار بازگشتی

یک {{domxref("DOMMatrix")}}.

## مثال‌ها

```js
const matrix = new DOMMatrixReadOnly().translate(13, 21);
const multipliedMatrix = matrix.multiply(matrix);
console.log(matrix.toString()); // output: matrix(1, 0, 0, 1, 13, 21)
console.log(multipliedMatrix.toString()); // output: matrix(1, 0, 0, 1, 26, 42)
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrix.multiplySelf()")}}
- {{domxref("DOMMatrix.preMultiplySelf()")}}
- تابع CSS {{CSSxRef("transform-function/matrix", "matrix()")}}
- تابع CSS {{CSSxRef("transform-function/matrix3d", "matrix3d()")}}