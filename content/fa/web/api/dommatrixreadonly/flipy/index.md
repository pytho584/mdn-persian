---
title: "DOMMatrixReadOnly: flipY() method"
short-title: flipY()
slug: Web/API/DOMMatrixReadOnly/flipY
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.flipY
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`flipY()`** در رابط {{domxref("DOMMatrixReadOnly")}} یک ماتریس جدید ایجاد می‌کند که حاصل وارونه‌سازی ماتریس اصلی حول محور Y است. این معادل ضرب ماتریس در `DOMMatrix(1, 0, 0, -1, 0, 0)` می‌باشد. ماتریس اصلی تغییر نمی‌کند.

## Syntax

```js-nolint
flipY()
```

### Parameters

هیچ.

### Return value

یک [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix).

## Examples

### وارونه‌سازی یک مثلث

در این مثال، SVG شامل دو [مسیر](/en-US/docs/Web/SVG/Reference/Attribute/d) یکسان به شکل مثلث است؛ هر دو با اندازه و موقعیت یکسان رسم شده‌اند. جعبه دید (viewBox) مقدار y منفی دارد که محتوای هر دو سمت محور Y را به ما نشان می‌دهد. این کار باعث می‌شود مثلث وارونه‌شده پس از تبدیل، در داخل دید قرار گیرد.

#### HTML

```html
<svg height="200" width="100" viewBox="0 -100 100 200">
  <path fill="red" d="M 0 0 L 100 0 L 50 100 Z" />
  <path fill="blue" d="M 0 0 L 100 0 L 50 100 Z" id="flipped" />
</svg>
```

#### JavaScript

جاوااسکریپت یک [ماتریس همانی](/en-US/docs/Web/API/DOMMatrixReadOnly/isIdentity) ایجاد می‌کند و سپس با استفاده از متد `flipY()` یک ماتریس جدید می‌سازد که روی مثلث آبی اعمال می‌شود و آن را حول محور Y وارونه می‌کند. مثلث قرمز در جای خود باقی می‌ماند.

```js
const flipped = document.getElementById("flipped");
const matrix = new DOMMatrix();
const flippedMatrix = matrix.flipY();
flipped.setAttribute("transform", flippedMatrix.toString());
```

#### Result

{{EmbedLiveSample('Inverting a triangle', '', '240')}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("DOMMatrixReadOnly.flipX()")}}