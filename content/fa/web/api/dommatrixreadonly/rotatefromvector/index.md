---
title: "DOMMatrixReadOnly: rotateFromVector() method"
short-title: rotateFromVector()
slug: Web/API/DOMMatrixReadOnly/rotateFromVector
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.rotateFromVector
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `rotateFromVector()` از رابط {{domxref("DOMMatrixReadOnly")}} یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با چرخش ماتریس مبدأ به اندازه زاویه بین بردار مشخص‌شده و `(1, 0)` ایجاد شده است. زاویه چرخش با زاویه بین بردار `(1,0)T` و `(x,y)T` در جهت عقربه‌های ساعت، یا `(+/-)arctan(y/x)` تعیین می‌شود. اگر `x` و `y` هر دو `0` باشند، زاویه `0` در نظر گرفته می‌شود. ماتریس اصلی تغییری نمی‌کند.

برای تغییر ماتریس در حین چرخاندن آن به اندازه زاویه بین بردار مشخص‌شده و `(1, 0)`، به {{domxref("DOMMatrix.rotateFromVectorSelf()")}} مراجعه کنید.

## نحو

```js-nolint
rotateFromVector()
rotateFromVector(rotX)
rotateFromVector(rotX, rotY)
```

### پارامترها

- `rotX` {{optional_inline}}
  - : یک عدد؛ مختصات x بردار (x,y) که زاویه چرخش را تعیین می‌کند. اگر تعریف نشده باشد، `0` استفاده می‌شود.
- `rotY` {{optional_inline}}
  - : یک عدد؛ مختصات y بردار (x,y) که زاویه چرخش را تعیین می‌کند. اگر تعریف نشده باشد، `0` استفاده می‌شود.

### مقدار بازگشتی

یک [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix).

## مثال‌ها

```js
const matrix = new DOMMatrix(); // create a matrix
console.log(matrix.toString()); // original value
// output: "matrix(1, 0, 0, 1, 0, 0)"

console.log(matrix.rotateFromVector().toString()); // defaults to `0`
// output: matrix(1, 0, 0, 1, 0, 0)

console.log(matrix.rotateFromVector(10, 20).toString());
// matrix(0.447, 0.894, -0.894, 0.447, 0, 0)

console.log(matrix.rotateFromVector(-5, 5).toString());
// matrix(-0.707, 0.707, -0.707, -0.707, 0, 0)

console.log(matrix.toString()); // matrix remains unchanged
// output: "matrix(1, 0, 0, 1, 0, 0)"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrix.rotateFromVectorSelf()")}}
- {{domxref("DOMMatrixReadOnly.rotate()")}}
- {{domxref("DOMMatrixReadOnly.rotateAxisAngle()")}}
- ویژگی {{cssxref("transform")}} در CSS و تابع {{cssxref("transform-function/rotate3d", "rotate3d()")}}
- ویژگی {{cssxref("rotate")}} در CSS
- ماژول [تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی `[transform](/en-US/docs/Web/SVG/Reference/Attribute/transform)` در SVG
- رابط {{domxref("CanvasRenderingContext2D")}} و متد {{domxref("CanvasRenderingContext2D.rotate()", "rotate()")}}