```
---
title: "DOMMatrixReadOnly: scale3d() method"
short-title: scale3d()
slug: Web/API/DOMMatrixReadOnly/scale3d
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.scale3d
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`scale3d()`** از رابط {{domxref("DOMMatrixReadOnly")}} یک ماتریس جدید ایجاد می‌کند که نتیجهٔ اعمال یک تبدیل مقیاس سه‌بعدی (3D scale) روی ماتریس است. این متد یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با مقیاس‌دادن ماتریس سه‌بعدی مبدأ با ضریب مقیاس داده‌شده و حول نقطهٔ مبدأ مشخص‌شده توسط پارامترهای origin ساخته می‌شود؛ مبدأ پیش‌فرض `(0, 0, 0)` است. ماتریس اصلی تغییری نمی‌کند.

برای تغییر ماتریس هنگام اعمال مقیاس سه‌بعدی، به {{domxref("DOMMatrix.scale3dSelf()")}} مراجعه کنید.

## نحو (Syntax)

```js-nolint
scale3d()
scale3d(scale)
scale3d(scale, originX)
scale3d(scale, originX, originY)
scale3d(scale, originX, originY, originZ)
```

### پارامترها

- `scale`
  - : یک ضریب؛ مقدار مقیاس. اگر مقداری برای scale داده نشود، پیش‌فرض آن `1` است.
- `originX` {{optional_inline}}
  - : مختصات x برای مبدأ تبدیل. اگر مبدأی داده نشود، پیش‌فرض آن `0` است.
- `originY` {{optional_inline}}
  - : مختصات y برای مبدأ تبدیل. اگر مبدأی داده نشود، پیش‌فرض آن `0` است.
- `originZ` {{optional_inline}}
  - : مختصات z برای مبدأ تبدیل. اگر این مقدار `0` باشد (که پیش‌فرض در صورت حذف‌شدن است)، ماتریس حاصل ممکن است سه‌بعدی نباشد.

### مقدار بازگشتی

یک {{domxref("DOMMatrix")}}.

## مثال‌ها

```js
const matrix = new DOMMatrix();
console.log(matrix.toString()); // no transforms applied
// matrix(1, 0, 0, 1, 0, 0)

console.log(matrix.scale3d(2).toString());
/* matrix3d(
    2, 0, 0, 0, 
    0, 2, 0, 0, 
    0, 0, 2, 0, 
    0, 0, 0, 1) */
console.log(matrix.scale3d(0.5, 25, 25, 1.25).toString());
/* matrix3d(
    0.5, 0, 0, 0, 
    0, 0.5, 0, 0, 
    0, 0, 0.5, 0, 1
    2.5, 12.5, 0.625, 1) */
console.log(matrix.toString()); // original matrix is unchanged
// matrix(1, 0, 0, 1, 0, 0)
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrix.scale3dSelf()")}}
- {{domxref("DOMMatrixReadOnly.scale()")}}
- ویژگی CSS {{cssxref("transform")}} و توابع {{cssxref("transform-function/scale3d", "scale3d()")}} و {{cssxref("transform-function/matrix3d", "matrix3d()")}}
- ماژول [تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform) در SVG
- متد {{domxref("CanvasRenderingContext2D.transform()")}} از رابط {{domxref("CanvasRenderingContext2D")}}
```