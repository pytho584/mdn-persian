---
title: "DOMMatrixReadOnly: inverse() method"
short-title: inverse()
slug: Web/API/DOMMatrixReadOnly/inverse
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.inverse
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`inverse()`** در رابط {{domxref("DOMMatrixReadOnly")}} ماتریس جدیدی می‌سازد که معکوس ماتریس اصلی است. اگر ماتریس قابل معکوس‌سازی نباشد، تمام مؤلفه‌های ماتریس جدید روی `NaN` تنظیم می‌شوند و ویژگی {{domxref("DOMMatrixReadOnly.is2D", "is2D")}} آن روی `false` قرار می‌گیرد. ماتریس اصلی تغییری نمی‌کند.

برای تغییر دادن ماتریس هنگام معکوس‌سازی، به {{domxref("DOMMatrix.invertSelf()")}} مراجعه کنید.

## نحو (Syntax)

```js-nolint
inverse()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{domxref("DOMMatrix")}}.

## مثال‌ها

```js
const matrix = new DOMMatrixReadOnly().rotate(30);
const invertedMatrix = matrix.inverse();
console.log(matrix.toString());
// خروجی: matrix(0.866, 0.5, -0.5, 0.866, 0, 0)
console.log(invertedMatrix.toString());
// خروجی: matrix(0.866, -0.5, 0.5, 0.866, 0, 0)
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrix.invertSelf()")}}
- {{domxref("DOMMatrixReadOnly.flipX()")}}
- {{domxref("DOMMatrixReadOnly.flipY()")}}
- تابع CSS {{CSSxRef("transform-function/matrix", "matrix()")}}
- تابع CSS {{CSSxRef("transform-function/matrix3d", "matrix3d()")}}