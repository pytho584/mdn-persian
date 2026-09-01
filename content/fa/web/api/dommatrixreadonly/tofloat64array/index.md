---
title: "DOMMatrixReadOnly: toFloat64Array() method"
short-title: toFloat64Array()
slug: Web/API/DOMMatrixReadOnly/toFloat64Array
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.toFloat64Array
---

{{APIRef("DOM")}}

متد **`toFloat64Array()`** از رابط {{domxref("DOMMatrixReadOnly")}} یک {{jsxref("Float64Array")}} جدید برمی‌گرداند که شامل هر ۱۶ عنصر (`m11`, `m12`, `m13`, `m14`, `m21`, `m22`, `m23`, `m24`, `m31`, `m32`, `m33`, `m34`, `m41`, `m42`, `m43`, `m44`) تشکیل‌دهندهٔ ماتریس است. این عناصر به صورت اعداد ممیز شناور با دقت دوگانه (double-precision floating-point) و به ترتیب ستون‌محور (دسترسی colexographical یا "colex") درون آرایه ذخیره می‌شوند. (به عبارت دیگر، از بالای ستون اول به پایین، سپس ستون دوم، و به همین ترتیب.)

## نحو

```js-nolint
toFloat64Array()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("Float64Array")}}؛ آرایه‌ای از ۱۶ مقدار عنصری ماتریس.

## مثال‌ها

```js
const matrix = new DOMMatrixReadOnly();
let float64 = matrix.translate(20, 30, 50).toFloat64Array();
console.log(float64); // Float64Array(16) [ 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 20, 30, 0, 1 ] ]
console.log(`m41: ${float64[12]}, m42: ${float64[13]}, m43: ${float64[14]}`); // m41: 20, m42: 30, M44: 40

float64 = matrix.rotate(30).toFloat64Array();
console.log(float64);
console.log(`m11: ${float64[0]}, m12: ${float64[1]}`); // m11: 0.8660254037844387, m12: 0.49999999999999994
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.toFloat32Array()")}}
- {{domxref("DOMMatrix.setMatrixValue()")}}