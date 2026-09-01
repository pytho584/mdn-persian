---
title: "DOMMatrixReadOnly: transformPoint() method"
short-title: transformPoint()
slug: Web/API/DOMMatrixReadOnly/transformPoint
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.transformPoint
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`transformPoint`** از رابط {{domxref("DOMMatrixReadOnly")}} یک شیء {{domxref("DOMPoint")}} جدید می‌سازد که با تبدیل یک نقطهٔ مشخص توسط ماتریس به دست می‌آید. نه خود ماتریس و نه نقطهٔ اصلی تغییری نمی‌کنند.

همچنین می‌توانید با اعمال ماتریس بر روی یک نقطه، با استفاده از متد {{domxref("DOMPointReadOnly.matrixTransform()")}} یک `DOMPoint` جدید ایجاد کنید.

## نحو

```js-nolint
transformPoint()
transformPoint(point)
```

### پارامترها

- `point`
  - : یک نمونهٔ `DOMPoint` یا `DOMPointReadOnly`، یا یک شیء حاوی حداکثر چهار ویژگی از موارد زیر:
    - `x`
      - : مختصهٔ `x` نقطه در فضا به‌صورت عدد. مقدار پیش‌فرض `0` است.
    - `y`
      - : مختصهٔ `y` نقطه در فضا به‌صورت عدد. مقدار پیش‌فرض `0` است.
    - `z`
      - : مختصهٔ `z` یا عمق نقطه در فضا به‌صورت عدد. مقدار پیش‌فرض `0` است؛ مقادیر مثبت به کاربر نزدیک‌تر و مقادیر منفی به سمت داخل صفحه عقب می‌روند.
    - `w`
      - : مقدار پرسپکتیو `w` نقطه به‌صورت عدد. مقدار پیش‌فرض `1` است.

### مقدار برگشتی

یک {{domxref("DOMPoint")}}.

## مثال‌ها

### تبدیل دوبعدی

```js
const matrix = new DOMMatrixReadOnly();
const point = new DOMPointReadOnly(10, 20); // DOMPointReadOnly {x: 10, y: 20, z: 0, w: 1}
let newPoint = matrix.transformPoint(point); // DOMPoint {x: 10, y: 20, z: 0, w: 1}
```

### تبدیل سه‌بعدی

در این مثال، یک نقطهٔ سه‌بعدی را بر روی یک ماتریس سه‌بعدی اعمال می‌کنیم:

```js
// Matrix with translate(22, 37, 10) applied
const matrix3D = new DOMMatrixReadOnly([
  1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 22, 37, 10, 1,
]);
const point3D = new DOMPointReadOnly(5, 10, 3); // DOMPointReadOnly {x: 5, y: 10, z: 3, w: 1}
const transformedPoint3D = point3D.matrixTransform(matrix3D); // DOMPoint {x: 27, y: 47, z: 13, w: 1}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMPointReadOnly.matrixTransform()")}}
- تابع‌های CSS {{cssxref("transform-function/matrix", "matrix()")}} و {{cssxref("transform-function/matrix3d", "matrix3d()")}}