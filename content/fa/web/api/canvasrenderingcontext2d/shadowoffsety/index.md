---
title: "CanvasRenderingContext2D: shadowOffsetY property"
short-title: shadowOffsetY
slug: Web/API/CanvasRenderingContext2D/shadowOffsetY
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.shadowOffsetY
---

{{APIRef("Canvas API")}}

خاصیت
**`CanvasRenderingContext2D.shadowOffsetY`**
در API Canvas 2D فاصله‌ای را مشخص می‌کند که سایه‌ها به صورت عمودی جابه‌جا می‌شوند.

> [!NOTE]
> سایه‌ها فقط زمانی رسم می‌شوند که خاصیت
> {{domxref("CanvasRenderingContext2D.shadowColor", "shadowColor")}} روی یک مقدار غیر شفاف تنظیم شده باشد. همچنین یکی از خاصیت‌های {{domxref("CanvasRenderingContext2D.shadowBlur", "shadowBlur")}}،
> {{domxref("CanvasRenderingContext2D.shadowOffsetX", "shadowOffsetX")}} یا `shadowOffsetY` باید غیر از صفر باشد.

## مقدار

یک عدد اعشاری (float) که فاصله‌ی جابه‌جایی عمودی سایه‌ها را مشخص می‌کند. مقادیر مثبت به سمت پایین و مقادیر منفی به سمت بالا هستند. مقدار پیش‌فرض `0` است (بدون جابه‌جایی عمودی). مقادیر {{jsxref("Infinity")}} و {{jsxref("NaN")}} نادیده گرفته می‌شوند.

## مثال‌ها

### جابه‌جایی عمودی سایه

این مثال یک سایه‌ی محو به یک مستطیل اضافه می‌کند. خاصیت
{{domxref("CanvasRenderingContext2D.shadowColor", "shadowColor")}} رنگ آن را تنظیم می‌کند،
`shadowOffsetY` جابه‌جایی آن را ۲۵ واحد به سمت پایین تنظیم می‌کند و
{{domxref("CanvasRenderingContext2D.shadowBlur", "shadowBlur")}} سطح محو شدگی ۱۰ را به آن می‌دهد.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// سایه
ctx.shadowColor = "red";
ctx.shadowOffsetY = 25;
ctx.shadowBlur = 10;

// مستطیل
ctx.fillStyle = "blue";
ctx.fillRect(20, 20, 150, 80);
```

#### نتیجه

{{ EmbedLiveSample('Moving_a_shadow_vertically', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این خاصیت: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.shadowOffsetX")}}
- {{domxref("CanvasRenderingContext2D.shadowColor")}}
- {{domxref("CanvasRenderingContext2D.shadowBlur")}}