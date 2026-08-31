---
title: "CanvasRenderingContext2D: isPointInStroke() method"
short-title: isPointInStroke()
slug: Web/API/CanvasRenderingContext2D/isPointInStroke
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.isPointInStroke
---

{{APIRef("Canvas API")}}

متد
**`CanvasRenderingContext2D.isPointInStroke()`**
از API بوم ۲ بعدی (Canvas 2D) گزارش می‌دهد که آیا نقطهٔ مشخص‌شده درون ناحیهٔ حاصل از ترسیم ضخامت (stroke) یک مسیر قرار دارد یا خیر.

## نحو (Syntax)

```js-nolint
isPointInStroke(x, y)
isPointInStroke(path, x, y)
```

### پارامترها

- `x`
  - : مختصات محور x نقطه‌ای که باید بررسی شود.
- `y`
  - : مختصات محور y نقطه‌ای که باید بررسی شود.
- `path`
  - : یک مسیر {{domxref("Path2D")}} که باید در برابر آن بررسی شود. اگر مشخص نشود، از مسیر جاری استفاده می‌شود.

### مقدار بازگشتی

یک مقدار بولی که اگر نقطه درون ناحیهٔ حاصل از ترسیم ضخامت مسیر باشد، `true` و در غیر این صورت `false` است.

## مثال‌ها

### بررسی یک نقطه در مسیر جاری

این مثال از متد `isPointInStroke()` برای بررسی اینکه آیا نقطه‌ای درون ناحیهٔ ضخامتِ مسیر جاری قرار دارد استفاده می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
<p>در ضخامت (stroke): <code id="result">false</code></p>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
const result = document.getElementById("result");

ctx.rect(10, 10, 100, 100);
ctx.stroke();
result.innerText = ctx.isPointInStroke(50, 10);
```

#### نتیجه

{{ EmbedLiveSample('Checking_a_point_in_the_current_path', 700, 220) }}

### بررسی یک نقطه در مسیر مشخص

هر بار که ماوس را حرکت می‌دهید، این مثال بررسی می‌کند که آیا مکان‌نما در ضخامتِ یک مسیر `Path2D` بیضوی قرار دارد یا خیر. اگر بله، رنگ ضخامت بیضی سبز می‌شود، در غیر این صورت قرمز است.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// ساخت بیضی
const ellipse = new Path2D();
ellipse.ellipse(150, 75, 40, 60, Math.PI * 0.25, 0, 2 * Math.PI);
ctx.lineWidth = 25;
ctx.strokeStyle = "red";
ctx.fill(ellipse);
ctx.stroke(ellipse);

// گوش دادن به حرکت ماوس
canvas.addEventListener("mousemove", (event) => {
  // بررسی اینکه آیا نقطه درون ضخامت بیضی است
  const isPointInStroke = ctx.isPointInStroke(
    ellipse,
    event.offsetX,
    event.offsetY,
  );
  ctx.strokeStyle = isPointInStroke ? "green" : "red";

  // رسم بیضی
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.fill(ellipse);
  ctx.stroke(ellipse);
});
```

#### نتیجه

{{ EmbedLiveSample('Checking_a_point_in_the_specified_path', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کنندهٔ این متد: {{domxref("CanvasRenderingContext2D")}}