---
title: "DOMMatrixReadOnly: toString() method"
short-title: toString()
slug: Web/API/DOMMatrixReadOnly/toString
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.toString
---

{{APIRef("DOM")}}

متد **`toString()`** به عنوان {{Glossary("stringifier")}} در رابط {{domxref("DOMMatrixReadOnly")}} مقدار ماتریس را به صورت یک رشته در قالب تابع تبدیل `matrix()` یا `matrix3d()` از [توابع تبدیل CSS](/en-US/docs/Web/CSS/Reference/Values/transform-function) برمی‌گرداند؛ یعنی فهرستی از مقادیر مختصات که با کاما جدا شده‌اند و به ترتیب با `"matrix(` یا `"matrix3d(` شروع و با `)"` پایان می‌یابند.

برای ماتریس دو بعدی، عناصر [`a` تا `f`](/en-US/docs/Web/API/DOMMatrix#a) فهرست می‌شوند؛ در مجموع شش مقدار به شکل `matrix(a, b, c, d, e, f)`. برای جزئیات این نحو، به تابع CSS {{cssxref("transform-function/matrix", "matrix()")}} مراجعه کنید.

برای ماتریس سه بعدی، رشته برگشتی شامل هر [۱۶ عنصر](/en-US/docs/Web/API/DOMMatrix#m11) است و به شکل `matrix3d(m11, m12, m13, m14, m21, m22, m23, m24, m31, m32, m33, m34, m41, m42, m43, m44)` است. برای جزئیات نحو نمادگذاری سه بعدی، به تابع CSS {{cssxref("transform-function/matrix3d", "matrix3d()")}} مراجعه کنید.

## Syntax

```js-nolint
toString()
```

### Parameters

هیچ.

### Return value

یک رشته؛ مقادیر فهرست که با کاما جدا شده‌اند و در قالب تابع `matrix()` یا `matrix3d()` قرار دارند.

## Examples

```js
const matrix = new DOMMatrixReadOnly();
console.log(matrix.translate(20, 30).toString()); // matrix(1, 0, 0, 1, 20, 30)
console.log(matrix.translate(30, 40, 50).toString()); // matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 30, 40, 50, 1)
console.log(matrix.skewY(15).skewX(5).rotate(3).translate(20, 50).toString());
// matrix(1.003, 0.321, 0.035, 1.01, 21.816, 56.824)
console.log(
  matrix.skewY(15).skewX(5).rotate(3).translate(20, 50, 60).toString(),
);
// matrix3d(1.003, 0.321, 0, 0, 0.0350, 1.008, 0, 0, 0, 0, 1, 0, 21.816, 56.824, 60, 1)
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("DOMMatrixReadOnly.toJSON()")}}
- {{domxref("DOMMatrix.setMatrixValue()")}}