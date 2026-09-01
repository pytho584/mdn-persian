---
title: "DOMMatrix: invertSelf() method"
short-title: invertSelf()
slug: Web/API/DOMMatrix/invertSelf
page-type: web-api-instance-method
browser-compat: api.DOMMatrix.invertSelf
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`invertSelf()`** از رابط {{domxref("DOMMatrix")}} ماتریس اصلی را معکوس می‌کند. اگر ماتریس قابل معکوس‌شدن نباشد، تمام مؤلفه‌های ماتریس جدید به `NaN` تنظیم شده و ویژگی {{domxref("DOMMatrixReadOnly.is2D", "is2D")}} آن به `false` تغییر می‌کند.

برای معکوس‌سازی یک ماتریس بدون تغییر آن، به {{domxref("DOMMatrixReadOnly.inverse()")}} مراجعه کنید.

## Syntax

```js-nolint
invertSelf()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{domxref("DOMMatrix")}}.

## مثال‌ها

در این مثال، یک ماتریس با چرخش ۳۰ درجه ایجاد می‌کنیم. سپس آن را معکوس می‌کنیم که نتیجه‌ی آن یک چرخش ۳۰- درجه است.

```js
const matrix = new DOMMatrix().rotate(30);
console.log(matrix.toString());
// خروجی: matrix(0.866, 0.5, -0.5, 0.866, 0, 0)
matrix.invertSelf();
console.log(matrix.toString());
// خروجی: matrix(0.866, -0.5, 0.5, 0.866, 0, 0)
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.inverse()")}}
- تابع CSS {{CSSxRef("transform-function/matrix", "matrix()")}}
- تابع CSS {{CSSxRef("transform-function/matrix3d", "matrix3d()")}}