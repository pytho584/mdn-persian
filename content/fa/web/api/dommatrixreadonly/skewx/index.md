---
title: "DOMMatrixReadOnly: skewX() method"
short-title: skewX()
slug: Web/API/DOMMatrixReadOnly/skewX
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.skewX
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `skewX()` از رابط {{domxref("DOMMatrixReadOnly")}} یک {{domxref("DOMMatrix")}} جدید بازمی‌گرداند که با اعمال تبدیل اریب (skew) مشخص‌شده به ماتریس مبدأ در امتداد محور x ایجاد شده است. ماتریس اصلی تغییر نمی‌کند.

برای تغییر مستقیم ماتریس هنگام اریب کردن آن در امتداد محور x، به {{domxref("DOMMatrix.skewXSelf()")}} مراجعه کنید.

## نحو (Syntax)

```js-nolint
skewX()
skewX(sX)
```

### پارامترها

- `sX`
  - : یک عدد؛ زاویه (بر حسب درجه) که ماتریس در امتداد محور x اریب می‌شود.

### مقدار بازگشتی

یک [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix).

## مثال‌ها

```js
const matrix = new DOMMatrix(); // create a matrix
console.log(matrix.toString()); // no transform applied
// "matrix(1, 0, 0, 1, 0, 0)"

console.log(matrix.skewX(14).toString());
// "matrix(1, 0, 0.25, 1, 0, 0)"

console.log(matrix.toString()); // original is unchanged
// "matrix(1, 0, 0, 1, 0, 0)"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.skewY()")}}
- {{domxref("DOMMatrix.skewXSelf()")}}
- ویژگی CSS {{cssxref("transform")}} و توابع {{cssxref("transform-function/skew", "skew()")}}، {{cssxref("transform-function/skewX", "skewX()")}} و {{cssxref("transform-function/matrix", "matrix()")}}
- ماژول [CSS transforms](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی SVG [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform)
- رابط {{domxref("CanvasRenderingContext2D")}} و متد {{domxref("CanvasRenderingContext2D.transform()", "transform()")}} آن