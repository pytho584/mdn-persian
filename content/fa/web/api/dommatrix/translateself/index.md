---
title: "DOMMatrix: translateSelf() method"
short-title: translateSelf()
slug: Web/API/DOMMatrix/translateSelf
page-type: web-api-instance-method
browser-compat: api.DOMMatrix.translateSelf
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد `translateSelf()` از رابط {{domxref("DOMMatrix")}} یک متد تبدیل تغییرپذیر (mutable) است که یک ماتریس را اصلاح می‌کند. این متد بردار(های) مشخص‌شده را اعمال کرده و ماتریس به‌روزشده را بازمی‌گرداند. بردار پیش‌فرض `[0, 0, 0]` است.

برای انتقال یک ماتریس بدون تغییر دادن آن، به {{domxref("DOMMatrixReadOnly.translate()")}} مراجعه کنید.

## نحو

```js-nolint
translateSelf(translateX, translateY)
translateSelf(translateX, translateY, translateZ)
```

### پارامترها

- `translateX`
  - : عددی که ابسیسا (مختصهٔ x) بردار انتقال را نشان می‌دهد.
- `translateY`
  - : عددی که مختصهٔ y بردار انتقال را نشان می‌دهد.
- `translateZ` {{optional_inline}}
  - : عددی که مؤلفهٔ z بردار انتقال را نشان می‌دهد. اگر ارائه نشود، پیش‌فرض آن 0 است. اگر این مقدار چیزی غیر از 0 باشد، ماتریس حاصل سه‌بعدی خواهد بود.

### مقدار بازگشتی

خود ماتریس را بازمی‌گرداند؛ یعنی همان [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix) که با بردار داده‌شده انتقال یافته است.

## مثال‌ها

```js
const matrix = new DOMMatrix(); // create a matrix
console.log(matrix.toString()); // output: "matrix(1, 0, 0, 1, 0, 0)"
matrix.translateSelf(25, 25); // mutate it
console.log(matrix); // output: "matrix(1, 0, 0, 1, 25, 25)"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.translate()")}}
- CSS {{cssxref("transform")}} property
- CSS {{cssxref("translate")}} property
- CSS {{cssxref("transform-function")}} functions
  - {{cssxref("transform-function/translate", "translate()")}}
  - {{cssxref("transform-function/translate3d", "translate3d()")}}
  - {{cssxref("transform-function/translateX", "translateX()")}}
  - {{cssxref("transform-function/translateY", "translateY()")}}
  - {{cssxref("transform-function/translateZ", "translateZ()")}}
- [CSS transforms](/en-US/docs/Web/CSS/Guides/Transforms) module
- SVG [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform) attribute
- {{domxref("CanvasRenderingContext2D")}} interface methods
  - {{domxref("CanvasRenderingContext2D.translate()")}}
  - {{domxref("CanvasRenderingContext2D.transform()")}}
  - {{domxref("CanvasRenderingContext2D.setTransform()")}}
  - {{domxref("CanvasRenderingContext2D.resetTransform()")}}