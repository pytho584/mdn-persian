---
title: "CanvasRenderingContext2D: strokeStyle property"
short-title: strokeStyle
slug: Web/API/CanvasRenderingContext2D/strokeStyle
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.strokeStyle
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.strokeStyle`** در Canvas 2D API تعیین می‌کند که برای خط‌های دور شکل‌ها (طرح کلی) از چه رنگ، گرادیان یا الگویی استفاده شود. مقدار پیش‌فرض `black` است.

> [!NOTE]
> برای مثال‌های بیشتر دربارهٔ استایل‌های خط و پر، به [اعمال استایل‌ها و رنگ‌ها](/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors) در [آموزش Canvas](/en-US/docs/Web/API/Canvas_API/Tutorial) مراجعه کنید.

## مقدار

یکی از موارد زیر:

- `color`
  - : رشته‌ای که به‌عنوان مقدار {{cssxref("&lt;color&gt;")}} در [CSS](/en-US/docs/Web/CSS) تفسیر می‌شود.
- `gradient`
  - : یک شیء {{domxref("CanvasGradient")}} (گرادیان خطی یا شعاعی).
- `pattern`
  - : یک شیء {{domxref("CanvasPattern")}} (تصویر تکرارشونده).

## مثال‌ها

### تغییر رنگ خط یک شکل

این مثال یک رنگ خط آبی را به یک مستطیل اعمال می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.strokeStyle = "blue";
ctx.strokeRect(10, 10, 100, 100);
```

#### نتیجه

{{ EmbedLiveSample('Changing_the_stroke_color_of_a_shape', 700, 160) }}

### ایجاد چندین رنگ خط با استفاده از حلقه‌ها

در این مثال، دو حلقهٔ `for` و متد {{domxref("CanvasRenderingContext2D.arc", "arc()")}} به کار رفته‌اند تا شبکه‌ای از دایره‌ها رسم شود که هرکدام رنگ خط متفاوتی دارند. برای این کار، از دو متغیر `i` و `j` استفاده می‌کنیم تا برای هر دایره یک رنگ RGB یکتا تولید کنیم و فقط مقادیر سبز و آبی را تغییر دهیم. (کانال قرمز مقدار ثابتی دارد.)

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js
const ctx = document.getElementById("canvas").getContext("2d");

for (let i = 0; i < 6; i++) {
  for (let j = 0; j < 6; j++) {
    ctx.strokeStyle = `rgb(
        0
        ${Math.floor(255 - 42.5 * i)}
        ${Math.floor(255 - 42.5 * j)})`;
    ctx.beginPath();
    ctx.arc(12.5 + j * 25, 12.5 + i * 25, 10, 0, Math.PI * 2, true);
    ctx.stroke();
  }
}
```

نتیجه به این شکل است:

{{EmbedLiveSample("Creating_multiple_stroke_colors_using_loops", "", "180")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

### نکتهٔ مخصوص WebKit/Blink

در مرورگرهای مبتنی بر WebKit و Blink، متد غیراستاندارد و منسوخ‌شدهٔ `ctx.setStrokeColor()` علاوه بر این ویژگی پیاده‌سازی شده است.

```js
setStrokeColor(color);
setStrokeColor(color, alpha);
setStrokeColor(grayLevel);
setStrokeColor(grayLevel, alpha);
setStrokeColor(r, g, b, a);
setStrokeColor(c, m, y, k, a);
```

## همچنین ببینید

- رابطِ تعریف‌کنندهٔ این ویژگی: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasGradient")}}
- {{domxref("CanvasPattern")}}