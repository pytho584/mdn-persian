---
title: "DOMMatrixReadOnly: fromFloat64Array() static method"
short-title: fromFloat64Array()
slug: Web/API/DOMMatrixReadOnly/fromFloat64Array_static
page-type: web-api-static-method
browser-compat: api.DOMMatrixReadOnly.fromFloat64Array_static
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد ایستای **`fromFloat64Array()`** در رابط {{domxref("DOMMatrixReadOnly")}} یک شیء جدید {{domxref("DOMMatrixReadOnly")}} از یک آرایه از اعداد اعشاری با دقت دوگانه (۶۴ بیتی) می‌سازد.

اگر آرایه ۶ مقدار داشته باشد، نتیجه یک ماتریس دوبعدی است؛ اگر آرایه ۱۶ مقدار داشته باشد، نتیجه یک ماتریس سه‌بعدی است. در غیر این صورت، استثنای {{jsxref("TypeError")}} پرتاب می‌شود.

## نحو

```js-nolint
DOMMatrixReadOnly.fromFloat64Array(array)
```

### پارامترها

- `array`
  - : یک {{jsxref("Float64Array")}} با ۶ یا ۱۶ عنصر به ترتیب ستون‌محور.

### مقدار بازگشتی

یک شیء {{domxref("DOMMatrixReadOnly")}}.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر طول پارامتر `array` برابر ۶ یا ۱۶ نباشد پرتاب می‌شود.

## مثال‌ها

### ساخت ماتریس دوبعدی از Float64Array

این مثال یک ماتریس دوبعدی از یک `Float64Array` با ۶ عنصر می‌سازد.

```js
const float64Array = new Float64Array([1, 0, 0, 1, 10, 20]);
const matrix2D = DOMMatrixReadOnly.fromFloat64Array(float64Array);

console.log(matrix2D.toString());
// Output: matrix(1, 0, 0, 1, 10, 20)

console.log(matrix2D.is2D);
// Output: true

console.log(matrix2D.e, matrix2D.f);
// Output: 10 20
```

### ساخت ماتریس سه‌بعدی از Float64Array

این مثال یک ماتریس سه‌بعدی از یک `Float64Array` با ۱۶ عنصر می‌سازد.

```js
const float64Array = new Float64Array([
  1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 10, 20, 30, 1,
]);
const matrix3D = DOMMatrixReadOnly.fromFloat64Array(float64Array);

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
- {{domxref("DOMMatrixReadOnly.fromFloat32Array_static", "DOMMatrixReadOnly.fromFloat32Array()")}}
- {{domxref("DOMMatrixReadOnly.fromMatrix_static", "DOMMatrixReadOnly.fromMatrix()")}}