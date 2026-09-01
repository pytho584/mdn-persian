---
title: "DOMMatrixReadOnly: toJSON() method"
short-title: toJSON()
slug: Web/API/DOMMatrixReadOnly/toJSON
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.toJSON
---

{{APIRef("DOM")}}

متد **`toJSON()`** از رابط {{domxref("DOMMatrixReadOnly")}} یک شیء {{jsxref("JSON")}} ساخته و بازمی‌گرداند. این شیء JSON شامل عناصر ماتریس ۲ بعدی `a` تا `f`، ۱۶ عنصر ماتریس ۴×۴ سه‌دی (`m[1-4][1-4]`) خاصیت بولی {{domxref("DOMMatrixReadOnly.is2D", "is2D")}} و خاصیت بولی {{domxref("DOMMatrixReadOnly.isIdentity", "isIdentity")}} است.

## نحو (Syntax)

```js-nolint
toJSON()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}}؛ نمایش JSON از شیء `DOMMatrixReadOnly`.

## مثال‌ها

```js
const matrix = new DOMMatrixReadOnly();
console.log(matrix.translate(20, 30).toJSON());
/*
{
    "a": 1,
    "b": 0,
    "c": 0,
    "d": 1,
    "e": 20,
    "f": 30,
    "m11": 1,
    "m12": 0,
    "m13": 0,
    "m14": 0,
    "m21": 0,
    "m22": 1,
    "m23": 0,
    "m24": 0,
    "m31": 0,
    "m32": 0,
    "m33": 1,
    "m34": 0,
    "m41": 20,
    "m42": 30,
    "m43": 0,
    "m44": 1,
    "is2D": true,
    "isIdentity": false
}
*/
console.log(matrix.translate(22, 55, 66).toJSON());
/*
{
    "a": 1,
    "b": 0,
    "c": 0,
    "d": 1,
    "e": 22,
    "f": 55,
    "m11": 1,
    "m12": 0,
    "m13": 0,
    "m14": 0,
    "m21": 0,
    "m22": 1,
    "m23": 0,
    "m24": 0,
    "m31": 0,
    "m32": 0,
    "m33": 1,
    "m34": 0,
    "m41": 22,
    "m42": 55,
    "m43": 66,
    "m44": 1,
    "is2D": false,
    "isIdentity": false
}
*/
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.toString()")}}
- {{domxref("DOMMatrix.setMatrixValue()")}}