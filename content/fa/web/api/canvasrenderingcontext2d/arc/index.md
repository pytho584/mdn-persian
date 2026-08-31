---
title: "CanvasRenderingContext2D: arc() method"
short-title: arc()
slug: Web/API/CanvasRenderingContext2D/arc
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.arc
---

{{APIRef("Canvas API")}}

متد
**`CanvasRenderingContext2D.arc()`**
از [Canvas 2D API](/en-US/docs/Web/API/CanvasRenderingContext2D) یک کمان دایره‌ای به زیرمسیر فعلی اضافه می‌کند.

## نحو

```js-nolint
arc(x, y, radius, startAngle, endAngle)
arc(x, y, radius, startAngle, endAngle, counterclockwise)
```

متد `arc()` یک کمان دایره‌ای با مرکز `(x, y)` و شعاع `radius` ایجاد می‌کند. مسیر از `startAngle` شروع می‌شود، به `endAngle` ختم می‌شود و در جهتی که توسط `counterclockwise` مشخص شده است حرکت می‌کند (پیش‌فرض: ساعتگرد).

### پارامترها

- `x`
  - : مختصات افقی مرکز کمان.
- `y`
  - : مختصات عمودی مرکز کمان.
- `radius`
  - : شعاع کمان. باید مثبت باشد.
- `startAngle`
  - : زاویهٔ شروع کمان بر حسب رادیان، که از محور مثبت x اندازه‌گیری می‌شود.
- `endAngle`
  - : زاویهٔ پایان کمان بر حسب رادیان، که از محور مثبت x اندازه‌گیری می‌شود.
- `counterclockwise` {{optional_inline}}
  - : یک مقدار بولی اختیاری. اگر `true` باشد، کمان را در خلاف جهت ساعتگرد بین زوایای شروع و پایان رسم می‌کند. مقدار پیش‌فرض `false` است (ساعتگرد).

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### رسم یک دایره کامل

این مثال با متد `arc()` یک دایرهٔ کامل رسم می‌کند.

#### HTML

```html
<canvas></canvas>
```

#### JavaScript

به کمان یک مختصات x برابر 100، مختصات y برابر 75 و شعاع 50 داده می‌شود. برای ایجاد یک دایرهٔ کامل، کمان از زاویهٔ 0 رادیان (0 درجه) شروع می‌شود و به زاویهٔ 2π رادیان (360 درجه) ختم می‌شود.

```js
const canvas = document.querySelector("canvas");
const ctx = canvas.getContext("2d");

ctx.beginPath();
ctx.arc(100, 75, 50, 0, 2 * Math.PI);
ctx.stroke();
```

#### نتیجه

{{ EmbedLiveSample('Drawing_a_full_circle', 700, 180) }}

### نمایش اشکال مختلف

این مثال اشکال گوناگونی را رسم می‌کند تا امکانات `arc()` را نشان دهد.

```html hidden
<canvas width="150" height="200"></canvas>
```

```js
const canvas = document.querySelector("canvas");
const ctx = canvas.getContext("2d");

// Draw shapes
for (let i = 0; i <= 3; i++) {
  for (let j = 0; j <= 2; j++) {
    ctx.beginPath();
    let x = 25 + j * 50; // x coordinate
    let y = 25 + i * 50; // y coordinate
    let radius = 20; // Arc radius
    let startAngle = 0; // Starting point on circle
    let endAngle = Math.PI + (Math.PI * j) / 2; // End point on circle
    let counterclockwise = i % 2 === 1; // Draw counterclockwise

    ctx.arc(x, y, radius, startAngle, endAngle, counterclockwise);

    if (i > 1) {
      ctx.fill();
    } else {
      ctx.stroke();
    }
  }
}
```

#### نتیجه

{{EmbedLiveSample('Different_shapes_demonstrated', "", "210")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کنندهٔ این متد: {{domxref("CanvasRenderingContext2D")}}
- برای ترسیم کمان بیضی از {{domxref("CanvasRenderingContext2D.ellipse()")}} استفاده کنید.