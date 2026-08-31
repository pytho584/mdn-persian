---
title: "CanvasRenderingContext2D: resetTransform() method"
short-title: resetTransform()
slug: Web/API/CanvasRenderingContext2D/resetTransform
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.resetTransform
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.resetTransform()`** در Canvas 2D API، تبدیل (transform) جاری را به ماتریس همانی (identity matrix) بازنشانی می‌کند.

## Syntax

```js-nolint
resetTransform()
```

### Parameters

هیچ.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

### بازنشانی ماتریس

در این مثال، یک مستطیل چرخیده پس از تغییر ماتریس رسم می‌شود و سپس ماتریس با استفاده از متد `resetTransform()` بازنشانی می‌شود.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

متد {{domxref("CanvasRenderingContext2D.rotate()", "rotate()")}} ماتریس تبدیل را به اندازه ۴۵ درجه می‌چرخاند. متد {{domxref("CanvasRenderingContext2D.fillRect()", "fillRect()")}} یک مستطیل توپر را با توجه به آن ماتریس رسم می‌کند.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Draw a rotated rectangle
ctx.rotate((45 * Math.PI) / 180);
ctx.fillRect(60, 0, 100, 30);

// Reset transformation matrix to the identity matrix
ctx.resetTransform();
```

#### Result

{{ EmbedLiveSample('Resetting_the_matrix', 700, 180) }}

### ادامه با ماتریس معمولی

هر زمان که رسم شکل‌های تبدیل‌شده را تمام کردید، باید قبل از رندر کردن هر چیز دیگری `resetTransform()` را فراخوانی کنید. در این مثال، دو شکل اول با تبدیل مایل (skew) و دو شکل آخر با تبدیل همانی (معمولی) رسم شده‌اند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Skewed rectangles
ctx.transform(1, 0, 1.7, 1, 0, 0);
ctx.fillStyle = "gray";
ctx.fillRect(40, 40, 50, 20);
ctx.fillRect(40, 90, 50, 20);

// Non-skewed rectangles
ctx.resetTransform();
ctx.fillStyle = "red";
ctx.fillRect(40, 40, 50, 20);
ctx.fillRect(40, 90, 50, 20);
```

#### Result

مستطیل‌های مایل خاکستری و مستطیل‌های غیرمایل قرمز هستند.

{{ EmbedLiveSample('Continuing_with_a_regular_matrix', 700, 180) }}

## Polyfill

همچنین می‌توانید از متد {{domxref("CanvasRenderingContext2D.setTransform()", "setTransform()")}} برای بازنشانی تبدیل فعلی به ماتریس همانی استفاده کنید، به این صورت:

```js
ctx.setTransform(1, 0, 0, 1, 0, 0);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رابطی که این متد را تعریف می‌کند: {{domxref("CanvasRenderingContext2D")}}