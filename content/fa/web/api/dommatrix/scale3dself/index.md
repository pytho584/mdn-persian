---
title: "DOMMatrix: scale3dSelf() method"
short-title: scale3dSelf()
slug: Web/API/DOMMatrix/scale3dSelf
page-type: web-api-instance-method
browser-compat: api.DOMMatrix.scale3dSelf
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`scale3dSelf()`** از رابط {{domxref("DOMMatrix")}} یک متد تغییرپذیر است که با اعمال یک ضریب مقیاس مشخص بر هر سه محور، حول مبدأ داده‌شده (با مبدأ پیش‌فرض `(0, 0, 0)`)، ماتریس را تغییر داده و ماتریس مقیاس‌یافته سه‌بعدی را برمی‌گرداند.

برای مقیاس‌دهی سه‌بعدی یک ماتریس بدون تغییر آن، به {{domxref("DOMMatrixReadOnly.scale3d()")}} مراجعه کنید که یک ماتریس مقیاس‌یافته جدید ایجاد می‌کند درحالی‌که ماتریس اصلی بدون تغییر می‌ماند.

## نحوه استفاده

```js-nolint
scale3dSelf()
scale3dSelf(scale)
scale3dSelf(scale, originX)
scale3dSelf(scale, originX, originY)
scale3dSelf(scale, originX, originY, originZ)
```

### پارامترها

- `scale`
  - : یک ضریب؛ مقدار مقیاس. اگر مقداری ارائه نشود، پیش‌فرض `1` است. اگر `scale` برابر `1` نباشد، ویژگی {{domxref("DOMMatrixReadOnly.is2D", "is2D")}} ماتریس جاری به `false` تنظیم می‌شود.
- `originX` {{optional_inline}}
  - : مختصات x برای مبدأ تبدیل. اگر مبدأ ارائه نشود، پیش‌فرض `0` است.
- `originY` {{optional_inline}}
  - : مختصات y برای مبدأ تبدیل. اگر مبدأ ارائه نشود، پیش‌فرض `0` است.
- `originZ` {{optional_inline}}
  - : مختصات z برای مبدأ تبدیل. اگر مبدأ ارائه نشود، پیش‌فرض `0` است.

### مقدار بازگشتی

خود ماتریس (یک {{domxref("DOMMatrix")}}) را برمی‌گرداند.

## مثال‌ها

```js
const matrix = new DOMMatrix();
console.log(matrix.scale3dSelf(2).toString());
/* matrix3d(
    2, 0, 0, 0, 
    0, 2, 0, 0, 
    0, 0, 2, 0, 
    0, 0, 0, 1) */
console.log(matrix.scale3dSelf(3.1, 25, 25, 1.25).toString());
/* matrix3d(
    6.2, 0, 0, 0,
    0, 6.2, 0, 0, 
    0, 0, 6.2, 0, 
    -105, -105, -5.25, 1) */
console.log(matrix.toString());
/* matrix3d(
    6.2, 0, 0, 0, 
    0, 6.2, 0, 0, 
    0, 0, 6.2, 0, 
    -105, -105, -5.25, 1) (همانند بالا) */
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("DOMMatrixReadOnly.scale3d()")}}
- {{domxref("DOMMatrix.scaleSelf()")}}
- ویژگی CSS {{cssxref("transform")}} و توابع {{cssxref("transform-function/scale3d", "scale3d()")}} و {{cssxref("transform-function/matrix3d", "matrix3d()")}}
- ماژول [تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی SVG [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform)
- رابط {{domxref("CanvasRenderingContext2D")}} و متد {{domxref("CanvasRenderingContext2D.transform()", "transform()")}}