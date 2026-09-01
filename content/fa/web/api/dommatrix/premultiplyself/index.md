---
title: "DOMMatrix: preMultiplySelf() method"
short-title: preMultiplySelf()
slug: Web/API/DOMMatrix/preMultiplySelf
page-type: web-api-instance-method
browser-compat: api.DOMMatrix.preMultiplySelf
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`preMultiplySelf()`** از رابط {{domxref("DOMMatrix")}}، ماتریس را با پیش‌ضرب کردن آن در `DOMMatrix` مشخص‌شده تغییر می‌دهد. این معادل حاصل‌ضرب `B⋅A` است، که در آن ماتریس `A` ماتریس مبدأ و ماتریس `B` ماتریسی است که به‌عنوان ورودی به متد داده می‌شود. اگر ماتریسی به‌عنوان ضریب مشخص نشود، ماتریس در ماتریسی ضرب می‌شود که همهٔ عناصر آن `0` هستند _به‌جز_ گوشهٔ پایین‑راست و عنصرِ بلافاصله بالای آن و عنصرِ سمت چپ آن: `m33` و `m34`. این دو عنصر مقدار پیش‌فرض `1` را دارند.

## سینتکس

```js-nolint
preMultiplySelf()
preMultiplySelf(otherMatrix)
```

### پارامترها

- `otherMatrix` {{optional_inline}}
  - : ضریب [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix).

### مقدار بازگشتی

خود ماتریس را برمی‌گرداند؛ یک [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix) که با نتایج ضرب‌های اعمال‌شده به‌روز شده است.

## مثال‌ها

```js
const matrix = new DOMMatrix().translate(3, 22);
const otherMatrix = new DOMMatrix().translateSelf(15, 45);

console.log(matrix.toString()); // output: matrix(1, 0, 0, 1, 3, 22)
console.log(otherMatrix.toString()); // output: matrix(1, 0, 0, 1, 15, 45)

matrix.preMultiplySelf(otherMatrix);

console.log(matrix.toString()); // output: matrix(1, 0, 0, 1, 18, 67)
console.log(otherMatrix.toString()); // output: matrix(1, 0, 0, 1, 15, 45)
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrix.multiplySelf()")}}
- {{domxref("DOMMatrixReadOnly.multiply()")}}
- تابع CSS {{CSSxRef("transform-function/matrix", "matrix()")}}
- تابع CSS {{CSSxRef("transform-function/matrix3d", "matrix3d()")}}