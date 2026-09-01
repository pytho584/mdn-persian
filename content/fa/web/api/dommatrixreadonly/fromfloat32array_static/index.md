---
title: "DOMMatrixReadOnly: fromFloat32Array() static method"
---

---
title: "DOMMatrixReadOnly: fromFloat32Array() static method"
short-title: fromFloat32Array()
slug: Web/API/DOMMatrixReadOnly/fromFloat32Array_static
page-type: web-api-static-method
browser-compat: api.DOMMatrixReadOnly.fromFloat32Array_static
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد ایستای **`fromFloat32Array()`** در رابط {{domxref("DOMMatrixReadOnly")}} یک شیء جدید {{domxref("DOMMatrixReadOnly")}} را با گرفتن آرایه‌ای از مقادیر ممیز شناور تک‌دقتی (32 بیتی) ایجاد می‌کند.

اگر آرایه ۶ مقدار داشته باشد، نتیجه یک ماتریس دوبعدی است؛ اگر ۱۶ مقدار داشته باشد، نتیجه یک ماتریس سه‌بعدی است. در غیر این صورت، استثنای {{jsxref("TypeError")}} پرتاب می‌شود.

## نحو

```js-nolint
DOMMatrixReadOnly.fromFloat32Array(array)
```

### پارامترها

- `array`
  - : یک {{jsxref("Float32Array")}} با ۶ یا ۱۶ عنصر به ترتیب ستون‌محور (column-major).

### مقدار بازگشتی

یک شیء {{domxref("DOMMatrixReadOnly")}}.

### استثناها

- {{jsxref("TypeError")}}
  - : زمانی پرتاب می‌شود که طول پارامتر `array` برابر ۶ یا ۱۶ نباشد.

## مثال‌ها

### ساخت ماتریس دوبعدی از یک Float32Array

این مثال یک ماتریس دوبعدی را از یک `Float32Array` شش‌عنصری می‌سازد.

```js
const float32Array = new Float32Array([1, 0, 0, 1, 10, 20]);
const matrix2D = DOMMatrixReadOnly.fromFloat32Array(float32Array);

console.log(matrix2D.toString());
// Output: matrix(1, 0, 0, 1, 10, 20)

console.log(matrix2D.is2D);
// Output: true
```

### ساخت ماتریس سه‌بعدی از یک Float32Array

این مثال یک ماتریس سه‌بعدی را از یک `Float32Array` شانزده‌عنصری می‌سازد.

```js
const float32Array = new Float32Array([
  1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 10, 20, 30, 1,
]);
const matrix3D = DOMMatrixReadOnly.fromFloat32Array(float32Array);

console.log(matrix3D.is2D);
// Output: false

console.log(matrix3D.m41, matrix3D.m42, matrix3D.m43);
// Output: 10 20 30
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly/DOMMatrixReadOnly", "DOMMatrixReadOnly()")}}
- {{domxref("DOMMatrixReadOnly.toFloat32Array()")}}
- {{domxref("DOMMatrixReadOnly.toFloat64Array()")}}
- {{domxref("DOMMatrixReadOnly.fromFloat64Array_static", "DOMMatrixReadOnly.fromFloat64Array()")}}
- {{domxref("DOMMatrixReadOnly.fromMatrix_static", "DOMMatrixReadOnly.fromMatrix()")}}