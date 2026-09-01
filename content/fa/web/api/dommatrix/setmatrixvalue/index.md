---
title: "DOMMatrix: setMatrixValue() method"
---

---
title: "DOMMatrix: setMatrixValue() method"
short-title: setMatrixValue()
slug: Web/API/DOMMatrix/setMatrixValue
page-type: web-api-instance-method
browser-compat: api.DOMMatrix.setMatrixValue
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`setMatrixValue()`** از رابط {{domxref("DOMMatrix")}} محتوای ماتریس را با ماتریسی که توسط تبدیل یا تبدیل‌های مشخص‌شده توصیف می‌شود جایگزین می‌کند و خود ماتریس را برمی‌گرداند.

## سینتکس

```js-nolint
setMatrixValue(transformList)
```

### پارامترها

- `transformList`
  - : یک رشته. مقدار آن از همان سینتکس مقدار ویژگی CSS {{cssxref("transform")}} پیروی می‌کند.

### مقدار بازگشتی

خود ماتریس را برمی‌گرداند؛ یعنی [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix) با مقادیر به‌روزرسانی‌شده.

## مثال‌ها

در این مثال، یک ماتریس می‌سازیم، با استفاده از متد {{domxref("DOMMatrix.translateSelf()")}} یک تبدیل سه‌بعدی روی آن اعمال می‌کنیم، با استفاده از متد `setMatrixValue()` آن را به یک تبدیل دوبعدی بازمی‌گردانیم و سپس با یک فراخوانی دیگر از متد `setMatrixValue()` دوباره به یک تبدیل سه‌بعدی برمی‌گردانیم.

```js
const matrix = new DOMMatrix();

console.log(matrix.toString()); // matrix(1, 0, 0, 1, 0, 0)
console.log(matrix.is2D); // true

matrix.translateSelf(30, 40, 50);
console.log(matrix.toString()); // matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 30, 40, 50, 1)
console.log(matrix.is2D); // false

matrix.setMatrixValue("matrix(1, 0, 0, 1, 15, 45)");
console.log(matrix.toString()); // output: matrix(1, 0, 0, 1, 15, 45)
console.log(matrix.is2D); // true

matrix.setMatrixValue(
  "matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 30, 40, 50, 1)",
);
console.log(matrix.toString()); // matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 30, 40, 50, 1)
console.log(matrix.is2D); // false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrix.translateSelf()")}}
- {{domxref("DOMMatrixReadOnly.is2D")}}
- تابع CSS {{CSSxRef("transform-function/matrix", "matrix()")}}
- تابع CSS {{CSSxRef("transform-function/matrix3d", "matrix3d()")}}