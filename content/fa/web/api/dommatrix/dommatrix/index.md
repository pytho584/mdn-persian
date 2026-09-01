---
title: "DOMMatrix: سازنده DOMMatrix()"
short-title: DOMMatrix()
slug: Web/API/DOMMatrix/DOMMatrix
page-type: web-api-constructor
browser-compat: api.DOMMatrix.DOMMatrix
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

سازنده **`DOMMatrix()`** یک شیء {{domxref("DOMMatrix")}} جدید ایجاد می‌کند که یک ماتریس ۴×۴ را نمایش می‌دهد و برای عملیات دو بعدی و سه بعدی مناسب است.

## نحو (Syntax)

```js-nolint
new DOMMatrix()
new DOMMatrix(initString)
new DOMMatrix(initArray)
```

### پارامترها

- `initString` {{optional_inline}}
  - : یک رشته که یک ماتریس دو بعدی یا سه بعدی را در قالب CSS {{cssxref("transform-function/matrix", "matrix()")}} یا {{cssxref("transform-function/matrix3d", "matrix3d()")}} نمایش می‌دهد.
- `initArray` {{optional_inline}}
  - : یک آرایه شامل ۶ یا ۱۶ عدد به ترتیب ستون‌محور (column-major). طول‌های دیگر آرایه باعث بروز {{jsxref("TypeError")}} می‌شوند.
    - یک آرایه ۶ عنصری به عنوان مؤلفه‌های ماتریس `[m11, m12, m21, m22, m41, m42]` تفسیر می‌شود که یک ماتریس دو بعدی ایجاد می‌کند.
    - یک آرایه ۱۶ عنصری به عنوان مؤلفه‌های ماتریس `[m11, m12, m13, m14, m21, m22, m23, m24, m31, m32, m33, m34, m41, m42, m43, m44]` تفسیر می‌شود که یک ماتریس سه بعدی ایجاد می‌کند.

    اگر این آرگومان حذف شود، یک ماتریس همانندی (identity matrix) ایجاد می‌شود، یعنی معادل `[1, 0, 0, 1, 0, 0]`.

    اگر این آرگومان به صورت {{jsxref("Float32Array")}} یا {{jsxref("Float64Array")}} ارائه شود، توصیه می‌شود از روش‌های ایستای (static) کارآمدتر {{domxref("DOMMatrix.fromFloat32Array_static", "DOMMatrix.fromFloat32Array()")}} یا {{domxref("DOMMatrix.fromFloat64Array_static", "DOMMatrix.fromFloat64Array()")}} استفاده کنید.

### مقدار بازگشتی

یک شیء {{domxref("DOMMatrix")}} جدید.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر آرگومان یک رشته نباشد یا یک آرایه با طولی غیر از ۶ یا ۱۶ باشد، پرتاب می‌شود.
- {{jsxref("SyntaxError")}}
  - : اگر آرگومان رشته‌ای در قالب معتبر CSS {{cssxref("transform-function/matrix", "matrix()")}} یا {{cssxref("transform-function/matrix3d", "matrix3d()")}} نباشد، پرتاب می‌شود.

## مثال‌ها

این مثال یک DOMMatrix ایجاد می‌کند تا به عنوان آرگومان برای فراخوانی {{domxref("DOMPointReadOnly.matrixTransform()")}} استفاده شود.

```js
const point = new DOMPoint(5, 4);
const scaleX = 2;
const scaleY = 3;
const translateX = 12;
const translateY = 8;
const angle = Math.PI / 2;
const matrix = new DOMMatrix([
  Math.cos(angle) * scaleX,
  Math.sin(angle) * scaleX,
  -Math.sin(angle) * scaleY,
  Math.cos(angle) * scaleY,
  translateX,
  translateY,
]);
const transformedPoint = point.matrixTransform(matrix);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrix.fromFloat32Array_static", "DOMMatrix.fromFloat32Array()")}}
- {{domxref("DOMMatrix.fromFloat64Array_static", "DOMMatrix.fromFloat64Array()")}}
- {{domxref("DOMMatrix.fromMatrix_static", "DOMMatrix.fromMatrix()")}}