---
title: "DOMMatrix: skewYSelf() method"
short-title: skewYSelf()
slug: Web/API/DOMMatrix/skewYSelf
page-type: web-api-instance-method
browser-compat: api.DOMMatrix.skewYSelf
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `skewYSelf()` از رابط {{domxref("DOMMatrix")}} یک متد تبدیل تغییرپذیر است که یک ماتریس را تغییر می‌دهد. این متد ماتریس اصلی را با اعمال تبدیل اریبِ مشخص‌شده در امتداد محور Y اریب می‌کند و ماتریس اریب‌شده را بازمی‌گرداند.

برای اریب‌کردن یک ماتریس در امتداد محور Y بدون تغییر دادن آن، به {{domxref("DOMMatrixReadOnly.skewY()")}} مراجعه کنید.

## نحو

```js-nolint
skewYSelf()
skewYSelf(sY)
```

### پارامترها

- `sY`
  - : یک عدد؛ زاویه‌ای بر حسب درجه که ماتریس بر اساس آن در امتداد محور Y اریب می‌شود.

### مقدار بازگشتی

خود ماتریس را برمی‌گرداند؛ همان [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix) که در امتداد محور Y به اندازهٔ زاویهٔ داده‌شده اریب شده است.

## مثال‌ها

```js
const matrix = new DOMMatrix(); // create a matrix
console.log(matrix.toString()); // output: "matrix(1, 0, 0, 1, 0, 0)"
matrix.skewYSelf(-14); // mutate it
console.log(matrix); // output: "matrix(1, -0.25, 0, 1, 0, 0)"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.skewY()")}}
- ویژگی CSS {{cssxref("transform")}}
- توابع CSS {{cssxref("transform-function")}}
  - {{cssxref("transform-function/skew", "skew()")}}
  - {{cssxref("transform-function/skewX", "skewX()")}}
  - {{cssxref("transform-function/skewY", "skewY()")}}
- ماژول [CSS transforms](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform) در SVG
- متدهای رابط {{domxref("CanvasRenderingContext2D")}}
  - {{domxref("CanvasRenderingContext2D.transform()")}}
  - {{domxref("CanvasRenderingContext2D.setTransform()")}}
  - {{domxref("CanvasRenderingContext2D.resetTransform()")}}