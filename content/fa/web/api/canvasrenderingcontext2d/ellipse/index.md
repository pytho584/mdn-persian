---
title: "CanvasRenderingContext2D: ellipse() method"
short-title: ellipse()
slug: Web/API/CanvasRenderingContext2D/ellipse
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.ellipse
---

{{APIRef("Canvas API")}}

متود **`CanvasRenderingContext2D.ellipse()`** در Canvas 2D API یک کمان بیضوی به زیرمسیر فعلی اضافه می‌کند.

## نحو (Syntax)

```js-nolint
ellipse(x, y, radiusX, radiusY, rotation, startAngle, endAngle)
ellipse(x, y, radiusX, radiusY, rotation, startAngle, endAngle, counterclockwise)
```

متود `ellipse()` یک کمان بیضوی با مرکز `(x, y)` و شعاع‌های `radiusX` و `radiusY` ایجاد می‌کند. مسیر از `startAngle` شروع شده و تا `endAngle` ادامه می‌یابد و در جهتی که توسط `counterclockwise` تعیین می‌شود حرکت می‌کند (پیش‌فرض در جهت عقربه‌های ساعت است).

### پارامترها

- `x`
  - : مختصات محور x (افقی) مرکز بیضی.
- `y`
  - : مختصات محور y (عمودی) مرکز بیضی.
- `radiusX`
  - : شعاع محور اصلی بیضی. باید غیرمنفی باشد.
- `radiusY`
  - : شعاع محور فرعی بیضی. باید غیرمنفی باشد.
- `rotation`
  - : چرخش بیضی، بر حسب رادیان.
- `startAngle`
  - : [زاویه خروج از مرکز](https://en.wikipedia.org/wiki/Angular_eccentricity) که بیضی از آن شروع می‌شود، در جهت عقربه‌های ساعت از محور x مثبت اندازه‌گیری شده و بر حسب رادیان بیان می‌شود.
- `endAngle`
  - : [زاویه خروج از مرکز](https://en.wikipedia.org/wiki/Angular_eccentricity) که بیضی در آن به پایان می‌رسد، در جهت عقربه‌های ساعت از محور x مثبت اندازه‌گیری شده و بر حسب رادیان بیان می‌شود.
- `counterclockwise` {{optional_inline}}
  - : یک مقدار بولی اختیاری که اگر `true` باشد، بیضی در خلاف جهت عقربه‌های ساعت رسم می‌شود. مقدار پیش‌فرض `false` (در جهت عقربه‌های ساعت) است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### رسم یک بیضی کامل

این مثال یک بیضی را با زاویه π/4 رادیان (۴۵ درجه) رسم می‌کند. برای رسم یک بیضی کامل، کمان از زاویه ۰ رادیان (۰ درجه) شروع شده و به زاویه ۲π رادیان (۳۶۰ درجه) ختم می‌شود.

#### HTML

```html
<canvas id="canvas" width="200" height="200"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Draw the ellipse
ctx.beginPath();
ctx.ellipse(100, 100, 50, 75, Math.PI / 4, 0, 2 * Math.PI);
ctx.stroke();

// Draw the ellipse's line of reflection
ctx.beginPath();
ctx.setLineDash([5, 5]);
ctx.moveTo(0, 200);
ctx.lineTo(200, 0);
ctx.stroke();
```

#### نتیجه

{{ EmbedLiveSample('Drawing_a_full_ellipse', 700, 250) }}

### کمان‌های بیضوی گوناگون

این مثال سه مسیر بیضوی با ویژگی‌های متفاوت ایجاد می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.fillStyle = "red";
ctx.beginPath();
ctx.ellipse(60, 75, 50, 30, Math.PI * 0.25, 0, Math.PI * 1.5);
ctx.fill();

ctx.fillStyle = "blue";
ctx.beginPath();
ctx.ellipse(150, 75, 50, 30, Math.PI * 0.25, 0, Math.PI);
ctx.fill();

ctx.fillStyle = "green";
ctx.beginPath();
ctx.ellipse(240, 75, 50, 30, Math.PI * 0.25, 0, Math.PI, true);
ctx.fill();
```

#### نتیجه

{{ EmbedLiveSample('Various_elliptical_arcs', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متود: {{domxref("CanvasRenderingContext2D")}}
- از {{domxref("CanvasRenderingContext2D.arc()")}} برای رسم کمان دایره‌ای استفاده کنید.