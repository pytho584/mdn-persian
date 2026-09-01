---
title: "DOMMatrixReadOnly: skewY() method"
---

---
title: "DOMMatrixReadOnly: skewY() method"
short-title: skewY()
slug: Web/API/DOMMatrixReadOnly/skewY
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.skewY
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `skewY()` از رابط {{domxref("DOMMatrixReadOnly")}} یک {{domatrix("DOMMatrix")}} جدید برمی‌گرداند که با اعمال تبدیل skew مشخص‌شده به ماتریس منبع در امتداد محور y ساخته شده است. ماتریس اصلی تغییر نمی‌کند.

برای تغییر دادن ماتریس هنگام skew کردن آن در امتداد محور y، به {{domxref("DOMMatrix.skewYSelf()")}} مراجعه کنید.

## نحو

```js-nolint
skewY()
skewY(sY)
```

### پارامترها

- `sY`
  - : یک عدد؛ زاویه‌ای بر حسب درجه که ماتریس در امتداد محور y با آن skew می‌شود.

### مقدار بازگشتی

یک [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix).

## مثال‌ها

```js
const matrix = new DOMMatrix(); // create a matrix
console.log(matrix.toString()); // original value
// "matrix(1, 0, 0, 1, 0, 0)"

console.log(matrix.skewY(14).toString()); // skew along y-axis
// "matrix(1, -0.25, 0, 1, 0, 0)"

console.log(matrix.toString()); // original unchanged
// "matrix(1, 0, 0, 1, 0, 0)"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrix.skewYSelf()")}}
- {{domxref("DOMMatrixReadOnly.skewX()")}}
- خصوصیت {{cssxref("transform")}} در CSS و تابع‌های {{cssxref("transform-function/skew", "skew()")}}، {{cssxref("transform-function/skewY", "skewY()")}} و {{cssxref("transform-function/matrix", "matrix()")}}
- ماژول [تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform) در SVG
- متد {{domxref("CanvasRenderingContext2D.transform()", "transform()")}} از رابط {{domxref("CanvasRenderingContext2D")}}