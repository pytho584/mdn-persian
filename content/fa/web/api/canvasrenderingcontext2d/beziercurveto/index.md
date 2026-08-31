---
title: "CanvasRenderingContext2D: bezierCurveTo() method"
short-title: bezierCurveTo()
slug: Web/API/CanvasRenderingContext2D/bezierCurveTo
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.bezierCurveTo
---

{{APIRef("Canvas API")}}

متد
**`CanvasRenderingContext2D.bezierCurveTo()`**
از Canvas 2D API یک منحنی [Bézier](/en-US/docs/Glossary/Bezier_curve) درجه سوم به زیرمسیر فعلی اضافه می‌کند. این متد به سه نقطه نیاز دارد: دو نقطه اول نقاط کنترل و نقطه سوم نقطه پایان هستند. نقطه شروع، آخرین نقطه در مسیر فعلی است که می‌توان قبل از ایجاد منحنی Bézier با استفاده از {{domxref("CanvasRenderingContext2D.moveTo", "moveTo()")}} آن را تغییر داد.

## نحو

```js-nolint
bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)
```

### پارامترها

- `cp1x`
  - : مختصات محور x اولین نقطه کنترل.
- `cp1y`
  - : مختصات محور y اولین نقطه کنترل.
- `cp2x`
  - : مختصات محور x دومین نقطه کنترل.
- `cp2y`
  - : مختصات محور y دومین نقطه کنترل.
- `x`
  - : مختصات محور x نقطه پایان.
- `y`
  - : مختصات محور y نقطه پایان.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

### نحوه کار bezierCurveTo

این مثال نحوه رسم یک منحنی Bézier درجه سوم را نشان می‌دهد.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
// تعریف بوم و زمینه
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// تعریف نقاط به صورت {x, y}
let start = { x: 50, y: 20 };
let cp1 = { x: 230, y: 30 };
let cp2 = { x: 150, y: 80 };
let end = { x: 250, y: 100 };

// منحنی Bézier درجه سوم
ctx.beginPath();
ctx.moveTo(start.x, start.y);
ctx.bezierCurveTo(cp1.x, cp1.y, cp2.x, cp2.y, end.x, end.y);
ctx.stroke();

// نقاط شروع و پایان
ctx.fillStyle = "blue";
ctx.beginPath();
ctx.arc(start.x, start.y, 5, 0, 2 * Math.PI); // نقطه شروع
ctx.arc(end.x, end.y, 5, 0, 2 * Math.PI); // نقطه پایان
ctx.fill();

// نقاط کنترل
ctx.fillStyle = "red";
ctx.beginPath();
ctx.arc(cp1.x, cp1.y, 5, 0, 2 * Math.PI); // نقطه کنترل اول
ctx.arc(cp2.x, cp2.y, 5, 0, 2 * Math.PI); // نقطه کنترل دوم
ctx.fill();
```

#### نتیجه

در این مثال، نقاط کنترل قرمز و نقاط
شروع و پایان آبی هستند.

{{ EmbedLiveSample('How_bezierCurveTo_works', 315, 165) }}

### یک منحنی Bézier ساده

این مثال یک منحنی Bézier ساده را با استفاده از `bezierCurveTo()` رسم می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

منحنی از نقطه مشخص شده توسط `moveTo()` یعنی (30, 30) شروع می‌شود. اولین
نقطه کنترل در (120, 160) و دومین نقطه در (180, 10) قرار می‌گیرد. منحنی در
(220, 140) به پایان می‌رسد.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.beginPath();
ctx.moveTo(30, 30);
ctx.bezierCurveTo(120, 160, 180, 10, 220, 140);
ctx.stroke();
```

#### نتیجه

{{ EmbedLiveSample('A_simple_Bézier_curve', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- [منحنی Bézier](/en-US/docs/Glossary/Bezier_curve)