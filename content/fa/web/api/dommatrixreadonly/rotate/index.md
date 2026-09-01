```markdown
---
title: "DOMMatrixReadOnly: rotate() method"
short-title: rotate()
slug: Web/API/DOMMatrixReadOnly/rotate
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.rotate
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `rotate()` در رابط {{domxref("DOMMatrixReadOnly")}} یک شیء {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با چرخاندن ماتریس مبدأ حول هر یک از محورهای آن به اندازه درجه‌های مشخص‌شده ایجاد می‌شود. ماتریس اصلی تغییری نمی‌کند.

برای تغییر ماتریس هنگام چرخاندن آن، به {{domxref("DOMMatrix.rotateSelf()")}} مراجعه کنید.

## نحو (Syntax)

```js-nolint
rotate()
rotate(rotX)
rotate(rotX, rotY)
rotate(rotX, rotY, rotZ)
```

### پارامترها

- `rotX`
  - : یک عدد؛ مختصه x بردار جهت‌دهنده محور چرخش. اگر غیرصفر باشد، [`is2D`](/en-US/docs/Web/API/DOMMatrixReadOnly/is2D) برابر `false` است.
- `rotY` {{optional_inline}}
  - : یک عدد؛ مختصه y بردار جهت‌دهنده محور چرخش. اگر غیرصفر باشد، [`is2D`](/en-US/docs/Web/API/DOMMatrixReadOnly/is2D) برابر `false` است.
- `rotZ` {{optional_inline}}
  - : یک عدد؛ مختصه z بردار جهت‌دهنده محور چرخش.

اگر فقط `rotX` ارسال شود، مقدار `rotX` به‌عنوان مختصه z در نظر گرفته می‌شود و هر دو مختصه x و y صفر تنظیم می‌شوند.

### مقدار بازگشتی

یک [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix).

## مثال‌ها

```js
const matrix = new DOMMatrix(); // create a matrix
console.log(matrix.toString());
// output: "matrix(1, 0, 0, 1, 0, 0)"

const rotated = matrix.rotate(30); // rotation and assignment
console.log(matrix.toString()); // original matrix is unchanged
// output: "matrix(1, 0, 0, 1, 0, 0)"
console.log(rotated.toString());
// output: "matrix(0.866, 0.5, -0.5, 0.866, 0, 0)"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrix.rotateSelf()")}}
- {{domxref("DOMMatrixReadOnly.rotateAxisAngle()")}}
- {{domxref("DOMMatrixReadOnly.rotateFromVector()")}}
- ویژگی CSS {{cssxref("transform")}} و تابع {{cssxref("transform-function/rotate3d", "rotate3d()")}}
- ویژگی CSS {{cssxref("rotate")}}
- ماژول [تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform) در SVG
- رابط {{domxref("CanvasRenderingContext2D")}} و متد {{domxref("CanvasRenderingContext2D.rotate()", "rotate()")}}
```