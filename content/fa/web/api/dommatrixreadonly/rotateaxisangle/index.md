---
title: "DOMMatrixReadOnly: rotateAxisAngle() method"
---

---
title: "DOMMatrixReadOnly: rotateAxisAngle() method"
short-title: rotateAxisAngle()
slug: Web/API/DOMMatrixReadOnly/rotateAxisAngle
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.rotateAxisAngle
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `rotateAxisAngle()` در رابط {{domxref("DOMMatrixReadOnly")}} یک {{domacro("DOMMatrix")}} جدید برمی‌گرداند که با چرخاندن ماتریس منبع حول بردار و زاویهٔ داده‌شده ساخته می‌شود. ماتریس اصلی تغییر نمی‌کند.

برای تغییر مستقیم ماتریس هنگام چرخش، به {{domxref("DOMMatrix.rotateAxisAngleSelf()")}} مراجعه کنید.

## Syntax

```js-nolint
rotateAxisAngle()
rotateAxisAngle(rotX)
rotateAxisAngle(rotX, rotY)
rotateAxisAngle(rotX, rotY, rotZ)
rotateAxisAngle(rotX, rotY, rotZ, angle)
```

### Parameters

- `rotX`
  - : یک عدد؛ مختصات x بردار محور چرخش. اگر غیرصفر باشد، {{domxref("DOMMatrixReadOnly.is2D", "is2D")}} برابر با `false` خواهد بود.
- `rotY` {{optional_inline}}
  - : یک عدد؛ مختصات y بردار محور چرخش. اگر `undefined` باشد، مقدار `rotX` استفاده می‌شود. اگر غیرصفر باشد، {{domxref("DOMMatrixReadOnly.is2D", "is2D")}} برابر با `false` خواهد بود.
- `rotZ` {{optional_inline}}
  - : یک عدد؛ مختصات z بردار محور چرخش. اگر `undefined` باشد، مقدار `rotX` استفاده می‌شود.
- `angle` {{optional_inline}}
  - : یک عدد؛ زاویهٔ چرخش حول بردار محور، بر حسب درجه.

### Return value

یک [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix).

## مثال‌ها

```js
const matrix = new DOMMatrix(); // create a matrix
console.log(matrix.rotateAxisAngle().toString()); // matrix(1, 0, 0, 1, 0, 0)
console.log(matrix.rotateAxisAngle(10, 20, 30).toString()); // matrix(1, 0, 0, 1, 0, 0)
console.log(matrix.rotateAxisAngle(10, 20, 30, 45).toString());
/* matrix3d(
    0.728, 0.609, -0.315, 0, 
    -0.525, 0.791, 0.315, 0, 
    0.441, -0.063, 0.895, 
    0, 0, 0, 0, 1) */
console.log(matrix.rotateAxisAngle(5, 5, 5, -45).toString());
/* matrix3d(
    0.805, -0.311, 0.506, 0, 
    0.506, 0.805, -0.311, 0, 
    -0.311, 0.506, 0.805, 0, 
    0, 0, 0, 1) */
console.log(matrix.toString()); // output: "matrix(1, 0, 0, 1, 0, 0)" (unchanged)
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrix.rotateAxisAngleSelf()")}}
- {{domxref("DOMMatrixReadOnly.rotate()")}}
- {{domxref("DOMMatrixReadOnly.rotateFromVector()")}}
- ویژگی CSS {{cssxref("transform")}} و تابع {{cssxref("transform-function/rotate3d", "rotate3d()")}}
- ویژگی CSS {{cssxref("rotate")}}
- ماژول [CSS transforms](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform) در SVG
- رابط {{domxref("CanvasRenderingContext2D")}} و متد {{domxref("CanvasRenderingContext2D.rotate()", "rotate()")}}