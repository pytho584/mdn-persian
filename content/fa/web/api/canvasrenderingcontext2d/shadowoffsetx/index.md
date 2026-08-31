---
title: "CanvasRenderingContext2D: shadowOffsetX property"
short-title: shadowOffsetX
slug: Web/API/CanvasRenderingContext2D/shadowOffsetX
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.shadowOffsetX
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.shadowOffsetX`** در Canvas 2D API فاصله‌ای را مشخص می‌کند که سایه‌ها به صورت افقی جابه‌جا می‌شوند.

> [!NOTE]
> سایه‌ها فقط زمانی رسم می‌شوند که ویژگی
> {{domxref("CanvasRenderingContext2D.shadowColor", "shadowColor")}} روی یک مقدار غیرشفاف تنظیم شده باشد. همچنین یکی از ویژگی‌های {{domxref("CanvasRenderingContext2D.shadowBlur", "shadowBlur")}}، `shadowOffsetX` یا
> {{domxref("CanvasRenderingContext2D.shadowOffsetY", "shadowOffsetY")}} باید غیرصفر باشد.

## مقدار

یک عدد اعشاری (float) که فاصله‌ی جابه‌جایی افقی سایه‌ها را مشخص می‌کند. مقادیر مثبت به سمت راست و مقادیر منفی به سمت چپ هستند. مقدار پیش‌فرض `0` است (بدون جابه‌جایی افقی). مقادیر {{jsxref("Infinity")}} و {{jsxref("NaN")}} نادیده گرفته می‌شوند.

## مثال‌ها

### جابه‌جایی افقی سایه

این مثال یک سایه‌ی محو به یک مستطیل اضافه می‌کند. ویژگی
{{domxref("CanvasRenderingContext2D.shadowColor", "shadowColor")}} رنگ آن را تنظیم می‌کند، `shadowOffsetX` جابه‌جایی آن را ۲۵ واحد به سمت راست مقداردهی می‌کند و
{{domxref("CanvasRenderingContext2D.shadowBlur", "shadowBlur")}} سطح محو شدگی ۱۰ را به آن می‌دهد.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Shadow
ctx.shadowColor = "red";
ctx.shadowOffsetX = 25;
ctx.shadowBlur = 10;

// Rectangle
ctx.fillStyle = "blue";
ctx.fillRect(20, 20, 150, 100);
```

#### نتیجه

{{ EmbedLiveSample('Moving_a_shadow_horizontally', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- واسط تعریف‌کننده‌ی این ویژگی: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.shadowOffsetY")}}
- {{domxref("CanvasRenderingContext2D.shadowColor")}}
- {{domxref("CanvasRenderingContext2D.shadowBlur")}}