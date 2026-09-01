---
title: "DOMMatrixReadOnly: isIdentity property"
---

---
title: "DOMMatrixReadOnly: isIdentity property"
short-title: isIdentity
slug: Web/API/DOMMatrixReadOnly/isIdentity
page-type: web-api-instance-property
browser-compat: api.DOMMatrixReadOnly.isIdentity
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

خصوصیت فقطخواندنی **`isIdentity`** از رابط {{domxref("DOMMatrixReadOnly")}} یک مقدار بولی است که اگر ماتریس، [identity matrix](https://en.wikipedia.org/wiki/Identity_matrix) باشد، مقدار آن `true` است.

ماتریس همانی ماتریسی است که همهٔ مقادیر آن `0` هستند، _بهجز_ مقادیر روی قطر اصلی از گوشهٔ بالا-چپ به گوشهٔ پایین-راست (به عبارت دیگر، جایی که فاصله‌ها در هر جهت با هم برابرند).

## مقدار

یک مقدار بولی.

## مثال‌ها

```js
// Initialize a 2D matrix
const matrix = new DOMMatrix(); // create a matrix
console.log(matrix.isIdentity); // output: true

// Apply a transform that has no effect
console.log(matrix.translate(0).isIdentity); // output: true

// Apply a transform with effect: this rotates the matrix by 30deg
console.log(matrix.rotate(30).isIdentity); // output: false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrix")}} interface
- {{domxref("CSSMatrixComponent")}} interface
- {{domxref("CanvasRenderingContext2D")}} interface
- CSS {{cssxref("transform-function/matrix()")}} function
- CSS {{cssxref("transform")}} property
- [CSS transforms](/en-US/docs/Web/CSS/Guides/Transforms) module
- SVG [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform) attribute
