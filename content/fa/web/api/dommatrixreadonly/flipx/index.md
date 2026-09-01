---
title: "DOMMatrixReadOnly: flipX() method"
short-title: flipX()
slug: Web/API/DOMMatrixReadOnly/flipX
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.flipX
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`flipX()`** در رابط {{domxref("DOMMatrixReadOnly")}} یک ماتریس جدید می‌سازد که نتیجه‌ی اعمال تبدیل ماتریس اصلی حول محور x است. این عمل معادل ضرب ماتریس در `DOMMatrix(-1, 0, 0, 1, 0, 0)` می‌باشد. ماتریس اصلی تغییری نمی‌کند.

## نحو (Syntax)

```js-nolint
flipX()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix) برمی‌گرداند.

## مثال‌ها

### وارونه‌کردن یک مثلث

در این مثال، SVG شامل دو مسیر به شکل مثلث است که هر دو در موقعیت یکسان رسم شده‌اند. توجه داشته باشید که مختصه‌ی x ویژگی `viewBox` منفی است، بنابراین محتوای هر دو سمت محور x را نشان می‌دهد.

#### HTML

```html
<svg width="100" height="100" viewBox="-50 0 100 100">
  <path fill="red" d="M 0 50 L 50 0 L 50 100 Z" />
  <path id="flipped" fill="blue" d="M 0 50 L 50 0 L 50 100 Z" />
</svg>
```

#### جاوااسکریپت

جاوااسکریپت ابتدا یک ماتریس همانی (identity matrix) می‌سازد، سپس با استفاده از متد `flipX()` یک ماتریس جدید ایجاد می‌کند که به مثلث آبی اعمال می‌شود و آن را حول محور x وارونه می‌کند. مثلث قرمز در جای خود باقی می‌ماند.

```js
const flipped = document.getElementById("flipped");
const matrix = new DOMMatrixReadOnly();
const flippedMatrix = matrix.flipX();
flipped.setAttribute("transform", flippedMatrix.toString());
```

#### نتیجه

{{EmbedLiveSample('Inverting a triangle')}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.flipY()")}}