---
title: "DOMMatrix: rotateSelf() method"
short-title: rotateSelf()
slug: Web/API/DOMMatrix/rotateSelf
page-type: web-api-instance-method
browser-compat: api.DOMMatrix.rotateSelf
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `rotateSelf()` از رابط {{domxref("DOMMatrix")}} یک متد تغییرپذیر (mutable) است که ماتریس را تغییر می‌دهد. این متد ماتریس مبدأ را به اندازه درجه‌های مشخص‌شده حول هر یک از محورهایش می‌چرخاند و ماتریس چرخیده را بازمی‌گرداند.

برای چرخاندن یک ماتریس بدون تغییر آن، به {{domxref("DOMMatrixReadOnly.rotate()")}} مراجعه کنید.

## نحو (Syntax)

```js-nolint
rotateSelf()
rotateSelf(rotX)
rotateSelf(rotX, rotY)
rotateSelf(rotX, rotY, rotZ)
```

### پارامترها

- `rotX`
  - : یک عدد؛ مختصه x بردار نشان‌دهنده محور چرخش.
- `rotY` {{optional_inline}}
  - : یک عدد؛ مختصه y بردار نشان‌دهنده محور چرخش.
- `rotZ` {{optional_inline}}
  - : یک عدد؛ مختصه z بردار نشان‌دهنده محور چرخش.

اگر فقط یک پارامتر ارسال شود، `rotZ` برابر با مقدار `rotX` خواهد بود و هر دو `rotX` و `rotY` برابر با `0` هستند و چرخش یک چرخش دوبعدی است. اگر `rotX` و `rotY` غیرصفر باشند، [`is2D`](/en-US/docs/Web/API/DOMMatrixReadOnly/is2D) برابر با `false` است.

### مقدار بازگشتی

خود ماتریس را بازمی‌گرداند؛ یعنی همان [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix) چرخیده با بردارهای داده‌شده.

## مثال‌ها

```js
const matrix = new DOMMatrix(); // create a matrix
console.log(matrix.toString()); // output: "matrix(1, 0, 0, 1, 0, 0)"
matrix.rotateSelf(30); // mutate it
console.log(matrix); // output: "matrix(0.866, 0.5, -0.5, 0.866, 0, 0)"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.rotate()")}}
- ویژگی CSS {{cssxref("transform")}}
- ویژگی CSS {{cssxref("rotate")}}
- توابع {{cssxref("transform-function")}} در CSS
  - {{cssxref("transform-function/rotate", "rotate()")}}
  - {{cssxref("transform-function/rotate3d", "rotate3d()")}}
  - {{cssxref("transform-function/rotateX", "rotateX()")}}
  - {{cssxref("transform-function/rotateY", "rotateY()")}}
  - {{cssxref("transform-function/rotateZ", "rotateZ()")}}
- ماژول [تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform) در SVG
- متدهای رابط {{domxref("CanvasRenderingContext2D")}}
  - {{domxref("CanvasRenderingContext2D.rotate()")}}
  - {{domxref("CanvasRenderingContext2D.transform()")}}
  - {{domxref("CanvasRenderingContext2D.setTransform()")}}
  - {{domxref("CanvasRenderingContext2D.resetTransform()")}}