---
title: "DOMMatrixReadOnly: DOMMatrixReadOnly() constructor"
---

---
title: "DOMMatrixReadOnly: DOMMatrixReadOnly() constructor"
short-title: DOMMatrixReadOnly()
slug: Web/API/DOMMatrixReadOnly/DOMMatrixReadOnly
page-type: web-api-constructor
browser-compat: api.DOMMatrixReadOnly.DOMMatrixReadOnly
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

سازندهٔ **`DOMMatrixReadOnly()`** یک شیء جدید {{domxref("DOMMatrixReadOnly")}} می‌سازد که یک ماتریس 4×4 را نشان می‌دهد و برای عملیات دوبعدی و سه‌بعدی مناسب است.

## Syntax

```js-nolint
new DOMMatrixReadOnly()
new DOMMatrixReadOnly(initString)
new DOMMatrixReadOnly(initArray)
```

### Parameters

- `initString` {{optional_inline}}
  - : رشته‌ای که یک ماتریس دوبعدی یا سه‌بعدی را در قالب CSS {{cssxref("transform-function/matrix", "matrix()")}} یا {{cssxref("transform-function/matrix3d", "matrix3d()")}} نشان می‌دهد.
- `initArray` {{optional_inline}}
  - : آرایه‌ای شامل ۶ یا ۱۶ عدد به ترتیب ستون‌محور (column-major). طول‌های دیگر آرایه یک {{jsxref("TypeError")}} ایجاد می‌کنند.
    - یک آرایهٔ ۶-عنصری به عنوان اجزای ماتریس `[m11, m12, m21, m22, m41, m42]` تفسیر می‌شود و یک ماتریس دوبعدی می‌سازد.
    - یک آرایهٔ ۱۶-عنصری به عنوان اجزای ماتریس `[m11, m12, m13, m14, m21, m22, m23, m24, m31, m32, m33, m34, m41, m42, m43, m44]` تفسیر می‌شود و یک ماتریس سه‌بعدی می‌سازد.

    اگر این آرگومان حذف شود، یک ماتریس همانی (identity matrix) ساخته می‌شود، یعنی معادل `[1, 0, 0, 1, 0, 0]`.

    اگر این آرگومان به صورت {{jsxref("Float32Array")}} یا {{jsxref("Float64Array")}} ارائه شود، بهتر است از روش‌های ایستای سریع‌تر {{domxref("DOMMatrixReadOnly.fromFloat32Array_static", "DOMMatrixReadOnly.fromFloat32Array()")}} یا {{domxref("DOMMatrixReadOnly.fromFloat64Array_static", "DOMMatrixReadOnly.fromFloat64Array()")}} استفاده کنید.

### Return value

یک شیء جدید {{domxref("DOMMatrixReadOnly")}}.

### Exceptions

- {{jsxref("TypeError")}}
  - : اگر آرگومان یک رشته نباشد یا آرایه‌ای با طولی غیر از ۶ یا ۱۶ باشد، پرتاب می‌شود.
- {{jsxref("SyntaxError")}}
  - : اگر آرگومان رشته‌ای در قالب معتبر CSS {{cssxref("transform-function/matrix", "matrix()")}} یا {{cssxref("transform-function/matrix3d", "matrix3d()")}} نباشد، پرتاب می‌شود.

## Examples

### Creating a DOMMatrixReadOnly from a string

```js
const matrixFromString = new DOMMatrixReadOnly("matrix(1, 0, 0, 1, 10, 20)");
console.log(matrixFromString.toJSON());
// Output: {a: 1, b: 0, c: 0, d: 1, e: 10, f: 20}
```

### Creating a DOMMatrixReadOnly from an array

```js
const matrixFromArray = new DOMMatrixReadOnly([1, 0, 0, 1, 10, 20]);
console.log(matrixFromArray.toJSON());
// Output: {a: 1, b: 0, c: 0, d: 1, e: 10, f: 20}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("DOMMatrixReadOnly.fromFloat32Array_static", "DOMMatrixReadOnly.fromFloat32Array()")}}
- {{domxref("DOMMatrixReadOnly.fromFloat64Array_static", "DOMMatrixReadOnly.fromFloat64Array()")}}
- {{domxref("DOMMatrixReadOnly.fromMatrix_static", "DOMMatrixReadOnly.fromMatrix()")}}