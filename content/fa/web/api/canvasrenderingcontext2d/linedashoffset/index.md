---
title: "CanvasRenderingContext2D: lineDashOffset property"
short-title: lineDashOffset
slug: Web/API/CanvasRenderingContext2D/lineDashOffset
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.lineDashOffset
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.lineDashOffset`** در Canvas 2D API، افست خط‌چین (یا «فاز») را تنظیم می‌کند.

> [!NOTE]
> خطوط با فراخوانی متد {{domxref("CanvasRenderingContext2D.stroke()", "stroke()")}} رسم می‌شوند.

## مقدار

یک عدد اعشاری که مقدار افست خط‌چین را مشخص می‌کند. مقدار پیش‌فرض `0.0` است.

## مثال‌ها

### جابجایی یک خط‌چین

این مثال دو خط چین رسم می‌کند. خط اول هیچ افستی ندارد و خط دوم دارای افست ۴ است.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.setLineDash([4, 16]);

// خط چین بدون افست
ctx.beginPath();
ctx.moveTo(0, 50);
ctx.lineTo(300, 50);
ctx.stroke();

// خط چین با افست ۴
ctx.beginPath();
ctx.strokeStyle = "red";
ctx.lineDashOffset = 4;
ctx.moveTo(0, 100);
ctx.lineTo(300, 100);
ctx.stroke();
```

#### نتیجه

خطی که دارای افست خط‌چین است به رنگ قرمز رسم شده است.

{{ EmbedLiveSample('Offsetting_a_line_dash', 700, 180) }}

### مورچه‌های راهپیمایی

اثر [مورچه‌های راهپیمایی](https://en.wikipedia.org/wiki/Marching_ants) یک تکنیک انیمیشن است که اغلب در ابزارهای انتخاب نرم‌افزارهای گرافیکی کامپیوتری دیده می‌شود. این تکنیک با متحرک‌سازی حاشیه، به کاربر کمک می‌کند تا مرز انتخاب را از پس‌زمینه تصویر تشخیص دهد.

```html hidden
<canvas id="canvas"></canvas>
```

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
let offset = 0;

function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.setLineDash([4, 2]);
  ctx.lineDashOffset = offset;
  ctx.strokeRect(10, 10, 100, 100);
}

function march() {
  offset++;
  if (offset > 5) {
    offset = 0;
  }
  draw();
  setTimeout(march, 20);
}

march();
```

{{ EmbedLiveSample('Marching_ants', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این ویژگی: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.getLineDash()")}}
- {{domxref("CanvasRenderingContext2D.setLineDash()")}}
- [اعمال سبک‌ها و رنگ‌ها](/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors)