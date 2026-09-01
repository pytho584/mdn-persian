---
title: "DOMMatrixReadOnly: is2D property"
short-title: is2D
slug: Web/API/DOMMatrixReadOnly/is2D
page-type: web-api-instance-property
browser-compat: api.DOMMatrixReadOnly.is2D
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

ویژگی فقط‑خواندنی **`is2D`** از رابط {{domxref("DOMMatrixReadOnly")}} یک پرچم بولی است که وقتی ماتریس دو‑بعدی باشد، `true` است. مقدار آن `true` است اگر ماتریس به‌عنوان یک ماتریس دو‑بعدی مقداردهی اولیه شده باشد و فقط عملیات تبدیل دو‑بعدی روی آن اعمال شده باشد. در غیر این صورت، ماتریس در سه‑بعد تعریف می‌شود و `is2D` برابر `false` است.

## مقدار

یک مقدار بولی.

## مثال‌ها

```js
// Initialize a 2D matrix
const matrix = new DOMMatrix(); // create a matrix
console.log(matrix.is2D); // output: true

// Transform in a 2D space
console.log(matrix.rotate(30).is2D); // output: true

// Apply a 3D transform
console.log(matrix.rotate(10, 20, 1).is2D); // output: false
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSTransformValue.is2D")}}
- {{domxref("CSSTransformComponent.is2D")}}
- توابع CSS {{cssxref("transform-function")}}
- ویژگی CSS {{cssxref("transform")}}
- ماژول [تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی SVG [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform)
- رابط {{domxref("CanvasRenderingContext2D")}}