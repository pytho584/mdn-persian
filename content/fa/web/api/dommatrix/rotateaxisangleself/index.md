---
title: "DOMMatrix: rotateAxisAngleSelf() method"
short-title: rotateAxisAngleSelf()
slug: Web/API/DOMMatrix/rotateAxisAngleSelf
page-type: web-api-instance-method
browser-compat: api.DOMMatrix.rotateAxisAngleSelf
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `rotateAxisAngleSelf()` از رابط {{domxref("DOMMatrix")}} یک متد تبدیل است که ماتریس مبدأ را با بردار و زاویه داده‌شده می‌چرخاند و ماتریس تغییر یافته را برمی‌گرداند.

برای چرخاندن یک ماتریس بدون تغییر آن، به {{domxref("DOMMatrixReadOnly.rotateAxisAngle()")}} مراجعه کنید که یک ماتریس چرخیده جدید ایجاد می‌کند و ماتریس اصلی را بدون تغییر باقی می‌گذارد.

## Syntax

```js-nolint
rotateAxisAngleSelf()
rotateAxisAngleSelf(rotX)
rotateAxisAngleSelf(rotX, rotY)
rotateAxisAngleSelf(rotX, rotY, rotZ)
rotateAxisAngleSelf(rotX, rotY, rotZ, angle)
```

### Parameters

- `rotX`
  - : یک عدد؛ مختصات x بردار مشخص‌کننده محور چرخش. اگر غیرصفر باشد، {{domxref("DOMMatrixReadOnly.is2D", "is2D")}} `false` است.
- `rotY` {{optional_inline}}
  - : یک عدد؛ مختصات y بردار مشخص‌کننده محور چرخش. اگر تعریف نشده باشد، مقدار `rotX` استفاده می‌شود. اگر غیرصفر باشد، {{domxref("DOMMatrixReadOnly.is2D", "is2D")}} `false` است.
- `rotZ` {{optional_inline}}
  - : یک عدد؛ مختصات z بردار مشخص‌کننده محور چرخش. اگر تعریف نشده باشد، مقدار `rotX` استفاده می‌شود.
- `angle` {{optional_inline}}
  - : یک عدد؛ زاویه چرخش حول بردار محور، بر حسب درجه.

اگر هر دو `rotY` و `rotZ` وجود نداشته باشند، `rotZ` به مقدار `rotX` تنظیم می‌شود و هر دو `rotX` و `rotY` برابر `0` می‌وند.

### Return value

یک [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix).

## Examples

```js
const matrix = new DOMMatrix(); // create a matrix
console.log(matrix.rotateAxisAngleSelf(10, 20, 30, 45).toString());
/* "matrix3d(
    0.728, 0.609, -0.315, 0, 
    -0.525, 0.791, 0.315, 0, 
    0.441, -0.063, 0.895, 
    0, 0, 0, 0, 1)" */
console.log(matrix.toString());
/* "matrix3d(
    0.728, 0.609, -0.315, 0, 
    -0.525, 0.791, 0.315, 0, 
    0.441, -0.063, 0.895, 0, 
    0, 0, 0, 1)" */
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("DOMMatrixReadOnly.rotateAxisAngle()")}}
- {{domxref("DOMMatrix.rotateSelf()")}}
- {{domxref("DOMMatrix.rotateFromVectorSelf()")}}
- ویژگی {{cssxref("transform")}} در CSS و تابع {{cssxref("transform-function/rotate3d", "rotate3d()")}}
- ویژگی {{cssxref("rotate")}} در CSS
- ماژول [CSS transforms](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی SVG [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform)
- رابط {{domxref("CanvasRenderingContext2D")}} و متد {{domxref("CanvasRenderingContext2D.rotate()", "rotate()")}}