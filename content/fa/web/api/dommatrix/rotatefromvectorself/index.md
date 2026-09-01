---
title: "DOMMatrix: متد rotateFromVectorSelf()"
short-title: rotateFromVectorSelf()
slug: Web/API/DOMMatrix/rotateFromVectorSelf
page-type: web-api-instance-method
browser-compat: api.DOMMatrix.rotateFromVectorSelf
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `rotateFromVectorSelf()` از رابط {{domxref("DOMMatrix")}} یک متد تبدیل تغییرپذیر است که ماتریس را با چرخاندن آن به اندازه زاویه بین بردار مشخص‌شده و `(1, 0)` تغییر می‌دهد. زاویه چرخش با زاویه بین بردار `(1,0)T` و `(x,y)T` در جهت عقربه‌های ساعت یا `(+/-)arctan(y/x)` تعیین می‌شود. اگر `x` و `y` هر دو `0` باشند، زاویه `0` در نظر گرفته شده و ماتریس تغییری نمی‌کند.

برای چرخاندن ماتریس از یک بردار بدون تغییر آن، به {{domxref("DOMMatrixReadOnly.rotateFromVector()")}} مراجعه کنید که یک ماتریس چرخیده جدید ایجاد می‌کند در حالی که ماتریس اصلی بدون تغییر می‌ماند.

## نحو

```js-nolint
rotateFromVectorSelf()
rotateFromVectorSelf(rotX)
rotateFromVectorSelf(rotX, rotY)
```

### پارامترها

- `rotX` {{optional_inline}}
  - : یک عدد؛ مختصات x از بردار x,y که زاویه چرخش را تعیین می‌کند. اگر تعریف نشده باشد، از `0` استفاده می‌شود.
- `rotY` {{optional_inline}}
  - : یک عدد؛ مختصات y از بردار x,y که زاویه چرخش را تعیین می‌کند. اگر تعریف نشده باشد، از `0` استفاده می‌شود.

### مقدار بازگشتی

خود ماتریس را برمی‌گرداند؛ [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix) به‌روزرسانی‌شده.

## مثال‌ها

```js
const matrix = new DOMMatrix(); // create a matrix
console.log(matrix.rotateFromVectorSelf().toString());
// output: matrix(1, 0, 0, 1, 0, 0) (no rotation applied)
console.log(matrix.rotateFromVectorSelf(10, 20).toString());
// output: matrix(0.447, 0.894, -0.894, 0.447, 0, 0)
console.log(matrix.toString());
// output: matrix(0.447, 0.894, -0.894, 0.447, 0, 0) (same as above)
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.rotateFromVector()")}}
- {{domxref("DOMMatrix.rotateSelf()")}}
- {{domxref("DOMMatrix.rotateAxisAngleSelf()")}}
- ویژگی CSS {{cssxref("transform")}} و تابع {{cssxref("transform-function/rotate3d", "rotate3d()")}}
- ویژگی CSS {{cssxref("rotate")}}
- ماژول [CSS transforms](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی SVG [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform)
- رابط {{domxref("CanvasRenderingContext2D")}} و متد {{domxref("CanvasRenderingContext2D.rotate()", "rotate()")}}