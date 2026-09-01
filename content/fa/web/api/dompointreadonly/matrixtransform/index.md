---
title: "DOMPointReadOnly: matrixTransform() method"
short-title: matrixTransform()
slug: Web/API/DOMPointReadOnly/matrixTransform
page-type: web-api-instance-method
browser-compat: api.DOMPointReadOnly.matrixTransform
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`matrixTransform()`** از رابط {{domxref("DOMPointReadOnly")}} یک تبدیل ماتریسی را که به‌صورت یک شیء مشخص شده است روی شیء `DOMPointReadOnly` اعمال می‌کند و یک شیء جدید `DOMPointReadOnly` می‌سازد و برمی‌گرداند. هیچ‌کدام از ماتریس و نقطه تغییر نمی‌کند.

اگر ماتریس ارسال‌شده به‌عنوان پارامتر دوبعدی باشد ({{domxref("DOMMatrixReadOnly.is2D", "is2D")}} برابر با `true` است)، این یک تبدیل دوبعدی خواهد بود و مختصات `z` نقطه برابر `0` و پرسپکتیو `w` نقطه برابر `1` خواهد بود. در غیر این صورت، این یک تبدیل سه‌بعدی است.

همچنین می‌توانید با استفاده از متد {{domxref("DOMMatrixReadOnly.transformPoint()")}} یک `DOMPoint` جدید از روی یک نقطه و یک ماتریس ایجاد کنید.

## سینتکس

```js-nolint
matrixTransform()
matrixTransform(matrix)
```

### پارامترها

- `matrix`
  - : یک شیء {{domxref("DOMMatrix")}} یا {{domxref("DOMMatrixReadOnly")}}.

### مقدار بازگشتی

یک شیء جدید {{domxref("DOMPoint")}}.

## مثال‌ها

### تبدیل دوبعدی

در این مثال، یک تبدیل ماتریسی دوبعدی را روی یک `DOMPointReadOnly` اعمال می‌کنیم که یک `DOMPoint` جدید می‌سازد:

```js
const originalPoint = new DOMPointReadOnly(10, 20); // DOMPointReadOnly {x: 10, y: 20, z: 0, w: 1}
const matrix = new DOMMatrix([1, 0, 0, 1, 15, 30]);

const transformedPoint = originalPoint.matrixTransform(matrix); // DOMPoint {x: 25, y: 50, z: 0, w: 1}

console.log(transformedPoint.toJSON()); // output: {x: 25, y: 50, z: 0, w: 1}
```

### تبدیل سه‌بعدی

در این مثال، یک تبدیل ماتریسی سه‌بعدی را روی یک `DOMPointReadOnly` اعمال می‌کنیم:

```js
const point = new DOMPointReadOnly(5, 10); // DOMPointReadOnly {x: 5, y: 10, z: 0, w: 1}
const matrix3D = new DOMMatrix().translate(0, 0, 10);
const transformedPoint = point.matrixTransform(matrix3D); // DOMPoint {x: 5, y: 10, z: 10, w: 1}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMPoint")}}
- {{domxref("DOMMatrix")}}
- {{domxref("DOMMatrixReadOnly.transformPoint()")}}
- توابع CSS {{cssxref("transform-function/matrix", "matrix()")}} و {{cssxref("transform-function/matrix3d", "matrix3d()")}}