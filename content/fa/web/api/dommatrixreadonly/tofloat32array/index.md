---
title: "DOMMatrixReadOnly: toFloat32Array() method"
short-title: toFloat32Array()
slug: Web/API/DOMMatrixReadOnly/toFloat32Array
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.toFloat32Array
---

{{APIRef("DOM")}}

متد **`toFloat32Array()`** از رابط {{domxref("DOMMatrixReadOnly")}} یک {{jsxref("Float32Array")}} جدید برمی‌گرداند که شامل تمام ۱۶ عنصر (`m11`, `m12`, `m13`, `m14`, `m21`, `m22`, `m23`, `m24`, `m31`, `m32`, `m33`, `m34`, `m41`, `m42`, `m43`, `m44`) تشکیل‌دهنده ماتریس است. عناصر به صورت اعداد ممیز شناور تک‌دقت (single-precision) در آرایه به ترتیب ستون‌محور (دسترسی کولکسوگرافیک، یا "colex") ذخیره می‌شوند. (به عبارت دیگر، ابتدا ستون اول از بالا به پایین، سپس ستون دوم، و به همین ترتیب.)

برای اعداد ممیز شناور دو‌دقت، به {{domxref("DOMMatrixReadOnly.toFloat64Array()")}} مراجعه کنید.

## نحو

```js-nolint
toFloat32Array()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Float32Array")}}؛ آرایه‌ای از ۱۶ مقدار عنصر ماتریس.

## مثال‌ها

### استفاده پایه

```js
const matrix = new DOMMatrixReadOnly();
const float32 = matrix.translate(20, 30, 50).toFloat32Array();
console.log(float32); // Float64Array(16) [ 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 20, 30, 0, 1 ] ]
console.log(`m41: ${float32[12]}, m42: ${float32[13]}, m43: ${float32[14]}`); // m41: 20, m42: 30, M44: 40
```

### تک‌دقت

روش‌های متعددی برای دسترسی به مقادیر یک ماتریس وجود دارد. این مثال یک ماتریس را به اندازه ۳۰ درجه می‌چرخاند، وضعیت چرخیده را به صورت یک شیء JSON با استفاده از متد {{domxref("DOMMatrixReadOnly.toJSON()")}} و به صورت یک آرایه تک‌دقت با استفاده از متد `toFloat32Array()` ذخیره می‌کند.

```js
const matrix = new DOMMatrixReadOnly();
const json = matrix.rotate(30).toJSON();
const float32 = matrix.rotate(30).toFloat32Array();

console.log(`a: ${json["a"]}, b: ${json["b"]}`); // a: 0.8660254037844387, b: 0.49999999999999994
console.log(`a: ${float32[0]}, b: ${float32[1]}`); // a: 0.8660253882408142, b: 0.5
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.toFloat64Array()")}}
- {{domxref("DOMMatrix.setMatrixValue()")}}