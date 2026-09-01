---
title: "DOMMatrix: skewXSelf() method"
short-title: skewXSelf()
slug: Web/API/DOMMatrix/skewXSelf
page-type: web-api-instance-method
browser-compat: api.DOMMatrix.skewXSelf
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `skewXSelf()` از رابط {{domxref("DOMMatrix")}} یک متد تغییردهندهٔ تغییرپذیر است که ماتریس را اصلاح می‌کند. این متد با اعمال تبدیل اریب‌سازی مشخص‌شده در امتداد محور X روی ماتریس مبدأ، آن را اریب می‌کند و ماتریس اریب‌شده را بازمی‌گرداند.

برای اریب کردن ماتریس در امتداد محور X بدون تغییر آن، به {{domxref("DOMMatrixReadOnly.skewX()")}} مراجعه کنید.

## نحو (Syntax)

```js-nolint
skewXSelf()
skewXSelf(sX)
```

### پارامترها

- `sX`
  - : یک عدد؛ زاویه بر حسب درجه که ماتریس باید در امتداد محور X بر اساس آن اریب شود.

### مقدار بازگشتی

خود ماتریس را بازمی‌گرداند؛ همان [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix) که با زاویهٔ داده‌شده در امتداد محور X اریب شده است.

## مثال‌ها

```js
const matrix = new DOMMatrix(); // create a matrix
console.log(matrix.toString()); // output: "matrix(1, 0, 0, 1, 0, 0)"
matrix.skewXSelf(14); // mutate it
console.log(matrix); // output: "matrix(1, 0, 0.25, 1, 0, 0)"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.skewX()")}}
- ویژگی CSS {{cssxref("transform")}}
- توابع {{cssxref("transform-function")}} در CSS
  - {{cssxref("transform-function/skew", "skew()")}}
  - {{cssxref("transform-function/skewX", "skewX()")}}
  - {{cssxref("transform-function/skewY", "skewY()")}}
- ماژول [تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform) در SVG
- متدهای رابط {{domxref("CanvasRenderingContext2D")}}
  - {{domxref("CanvasRenderingContext2D.transform()")}}
  - {{domxref("CanvasRenderingContext2D.setTransform()")}}
  - {{domxref("CanvasRenderingContext2D.resetTransform()")}}