```
---
title: "DOMMatrix: multiplySelf() method"
short-title: multiplySelf()
slug: Web/API/DOMMatrix/multiplySelf
page-type: web-api-instance-method
browser-compat: api.DOMMatrix.multiplySelf
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`multiplySelf()`** از رابط {{domxref("DOMMatrix")}}، ماتریس جاری را در پارامتر `otherMatrix` ضرب می‌کند و ضرب داخلی ماتریس اصلی و ماتریس داده‌شده را محاسبه می‌نماید: `A⋅B`. اگر ماتریسی به‌عنوان ضریب مشخص نشود، ماتریس در ماتریسی ضرب خواهد شد که تمام عناصر آن `0` هستند، _به‌جز_ گوشه‌ی پایین‌راست و عنصری که بلافاصله بالای آن و سمت چپ آن قرار دارد: `m33` و `m34`. این دو عنصر به‌طور پیش‌فرض مقدار `1` دارند.

برای ضرب یک ماتریس بدون تغییر دادن آن، به {{domxref("DOMMatrixReadOnly.multiply()")}} مراجعه کنید.

## سینتکس

```js-nolint
multiplySelf()
multiplySelf(otherMatrix)
```

### پارامترها

- `otherMatrix` {{optional_inline}}
  - یک [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix) به‌عنوان ضریب.

### مقدار بازگشتی

خود ماتریس را برمی‌گرداند؛ یعنی همان [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix) که با نتایج ضرب‌های اعمال‌شده به‌روزرسانی شده است.

## مثال‌ها

```js
const matrix = new DOMMatrix().rotate(30);

console.log(matrix.toString());
// output: matrix(0.866, 0.5, -0.5, 0.866, 0, 0)

matrix.multiplySelf(matrix);

console.log(matrix.toString());
// output: matrix(0.5, 0.866, -0.866, 0.5, 0, 0) (a 60deg rotation)
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.multiply()")}}
- {{domxref("DOMMatrix.preMultiplySelf()")}}
- تابع CSS {{CSSxRef("transform-function/matrix", "matrix()")}}
- تابع CSS {{CSSxRef("transform-function/matrix3d", "matrix3d()")}}
```