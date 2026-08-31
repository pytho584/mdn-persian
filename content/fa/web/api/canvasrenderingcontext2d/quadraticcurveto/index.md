---
title: "CanvasRenderingContext2D: quadraticCurveTo() method"
short-title: quadraticCurveTo()
slug: Web/API/CanvasRenderingContext2D/quadraticCurveTo
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.quadraticCurveTo
---

{{APIRef("Canvas API")}}

متد
**`CanvasRenderingContext2D.quadraticCurveTo()`**
از API Canvas 2D، یک [منحنی بزیه](/en-US/docs/Glossary/Bezier_curve) درجه دوم به زیرمسیر فعلی اضافه می‌کند.
این متد به دو نقطه نیاز دارد: نقطه اول نقطهٔ کنترل و نقطه دوم نقطهٔ پایان است. نقطهٔ شروع، آخرین نقطه در مسیر فعلی است که می‌توان آن را قبل از ایجاد منحنی بزیه درجه دوم با استفاده از {{domxref("CanvasRenderingContext2D.moveTo", "moveTo()")}} تغییر داد.

## Syntax

```js-nolint
quadraticCurveTo(cpx, cpy, x, y)
```

### پارامترها

- `cpx`
  - : مختصات محور x نقطهٔ کنترل.
- `cpy`
  - : مختصات محور y نقطهٔ کنترل.
- `x`
  - : مختصات محور x نقطهٔ پایان.
- `y`
  - : مختصات محور y نقطهٔ پایان.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### نحوه کارکرد quadraticCurveTo

این مثال نشان می‌دهد که چگونه یک منحنی بزیه درجه دوم رسم می‌شود.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Quadratic Bézier curve
ctx.beginPath();
ctx.moveTo(50, 20);
ctx.quadraticCurveTo(230, 30, 50, 100);
ctx.stroke();

// Start and end points
ctx.fillStyle = "blue";
ctx.beginPath();
ctx.arc(50, 20, 5, 0, 2 * Math.PI); // Start point
ctx.arc(50, 100, 5, 0, 2 * Math.PI); // End point
ctx.fill();

// Control point
ctx.fillStyle = "red";
ctx.beginPath();
ctx.arc(230, 30, 5, 0, 2 * Math.PI);
ctx.fill();
```

#### نتیجه

در این مثال، نقطهٔ کنترل قرمز و نقاط شروع و پایان آبی هستند.

{{ EmbedLiveSample('How_quadraticCurveTo_works', 315, 165) }}

### یک منحنی درجه دوم ساده

این مثال یک منحنی بزیه درجه دوم ساده را با استفاده از
`quadraticCurveTo()` رسم می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

منحنی از نقطه‌ای که توسط `moveTo()` مشخص شده شروع می‌شود: (20, 110). نقطهٔ کنترل در (230, 150) قرار می‌گیرد. منحنی در (250, 20) پایان می‌یابد.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.beginPath();
ctx.moveTo(20, 110);
ctx.quadraticCurveTo(230, 150, 250, 20);
ctx.stroke();
```

#### نتیجه

{{ EmbedLiveSample('A_simple_quadratic_curve', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- [منحنی بزیه](/en-US/docs/Glossary/Bezier_curve)