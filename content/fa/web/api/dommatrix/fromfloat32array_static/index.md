---
title: "DOMMatrix: fromFloat32Array() static method"
short-title: fromFloat32Array()
slug: Web/API/DOMMatrix/fromFloat32Array_static
page-type: web-api-static-method
browser-compat: api.DOMMatrix.fromFloat32Array_static
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد ایستایی **`fromFloat32Array()`** از رابط {{domxref("DOMMatrix")}} یک شیء جدید {{domxref("DOMMatrix")}} از روی یک آرایه از اعداد اعشاری با دقت تک (۳۲ بیتی) می‌سازد.

اگر آرایه ۶ مقدار داشته باشد، نتیجه یک ماتریس دوبعدی است؛ اگر ۱۶ مقدار داشته باشد، نتیجه یک ماتریس سه‌بعدی است. در غیر این صورت، یک استثنای {{jsxref("TypeError")}} پرتاب می‌شود.

## Syntax

```js-nolint
DOMMatrix.fromFloat32Array(array)
```

### Parameters

- `array`
  - : یک {{jsxref("Float32Array")}} با ۶ یا ۱۶ عنصر به ترتیب ستون‌محور (column-major).

### Return value

یک شیء {{domxref("DOMMatrix")}}.

### Exceptions

- {{jsxref("TypeError")}}
  - : اگر طول پارامتر `array` برابر ۶ یا ۱۶ نباشد پرتاب می‌شود.

## Examples

### ساخت ماتریس دوبعدی از یک Float32Array

این مثال یک ماتریس دوبعدی از یک `Float32Array` شش‌عنصری می‌سازد.

```js
const float32Array = new Float32Array([1, 0, 0, 1, 10, 20]);
const matrix2D = DOMMatrix.fromFloat32Array(float32Array);

console.log(matrix2D.toString());
// Output: matrix(1, 0, 0, 1, 10, 20)

console.log(matrix2D.is2D);
// Output: true
```

### ساخت ماتریس سه‌بعدی از یک Float32Array

این مثال یک ماتریس سه‌بعدی از یک `Float32Array` شانزده‌عنصری می‌سازد.

```js
const float32Array = new Float32Array([
  1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 10, 20, 30, 1,
]);
const matrix3D = DOMMatrix.fromFloat32Array(float32Array);

console.log(matrix3D.is2D);
// Output: false

console.log(matrix3D.m41, matrix3D.m42, matrix3D.m43);
// Output: 10 20 30
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("DOMMatrix/DOMMatrix", "DOMMatrix()")}}
- {{domxref("DOMMatrixReadOnly.toFloat32Array()")}}
- {{domxref("DOMMatrixReadOnly.toFloat64Array()")}}
- {{domxref("DOMMatrix.fromFloat64Array_static", "DOMMatrix.fromFloat64Array()")}}
- {{domxref("DOMMatrix.fromMatrix_static", "DOMMatrix.fromMatrix()")}}