---
title: "CanvasRenderingContext2D: fillStyle property"
short-title: fillStyle
slug: Web/API/CanvasRenderingContext2D/fillStyle
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.fillStyle
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.fillStyle`** در [Canvas 2D API](/en-US/docs/Web/API/Canvas_API) رنگ، گرادیان یا الگوی مورد استفاده برای پر کردن داخل اشکال را مشخص می‌کند. مقدار پیش‌فرض آن `black` است.

> [!NOTE]
> برای مثال‌های بیشتر درباره سبک‌های پر و Stroke، به بخش [اعمال سبک‌ها و رنگ‌ها](/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors) در [آموزش Canvas](/en-US/docs/Web/API/Canvas_API/Tutorial) مراجعه کنید.

## مقدار

یکی از موارد زیر:

- یک رشته که به عنوان مقدار CSS {{cssxref("&lt;color&gt;")}} تفسیر می‌شود.
- یک شیء {{domxref("CanvasGradient")}} (گرادیان خطی یا شعاعی).
- یک شیء {{domxref("CanvasPattern")}} (تصویر تکراری).

## مثال‌ها

### تغییر رنگ پر یک شکل

این مثال یک رنگ پر آبی را به یک مستطیل اعمال می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.fillStyle = "blue";
ctx.fillRect(10, 10, 100, 100);
```

#### نتیجه

{{ EmbedLiveSample('Changing_the_fill_color_of_a_shape', 700, 160) }}

### ایجاد چندین رنگ پر با استفاده از حلقه‌ها

در این مثال، از دو حلقه `for` برای رسم یک شبکه از مستطیل‌ها استفاده می‌کنیم که هر کدام رنگ پر متفاوتی دارند. برای این کار، از دو متغیر `i` و `j` برای تولید یک رنگ RGB منحصربه‌فرد برای هر مربع استفاده می‌کنیم و فقط مقادیر قرمز و سبز را تغییر می‌دهیم (کانال آبی مقدار ثابتی دارد). با تغییر کانال‌ها می‌توانید انواع پالت‌ها را ایجاد کنید.

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

for (let i = 0; i < 6; i++) {
  for (let j = 0; j < 6; j++) {
    ctx.fillStyle = `rgb(
        ${Math.floor(255 - 42.5 * i)}
        ${Math.floor(255 - 42.5 * j)}
        0)`;
    ctx.fillRect(j * 25, i * 25, 25, 25);
  }
}
```

نتیجه به شکل زیر است:

{{EmbedLiveSample("Creating_multiple_fill_colors_using_loops", "", "160")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

### نکته مخصوص WebKit/Blink

در مرورگرهای مبتنی بر WebKit و Blink، علاوه بر این ویژگی، متد غیراستاندارد و منسوخ `ctx.setFillColor()` نیز پیاده‌سازی شده است.

```js
setFillColor(color, /* (اختیاری) */ alpha);
setFillColor(grayLevel, /* (اختیاری) */ alpha);
setFillColor(r, g, b, a);
setFillColor(c, m, y, k, a);
```

## همچنین ببینید

- [Canvas API](/en-US/docs/Web/API/Canvas_API)
- رابط تعریف‌کننده این ویژگی: {{domxref("CanvasRenderingContext2D")}}
- مقادیر استفاده شده توسط این ویژگی:
  - نوع داده CSS {{cssxref("&lt;color&gt;")}}
  - شیء {{domxref("CanvasGradient")}}
  - شیء {{domxref("CanvasPattern")}}