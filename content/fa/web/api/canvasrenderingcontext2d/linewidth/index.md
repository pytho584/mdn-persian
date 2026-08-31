---
title: "CanvasRenderingContext2D: lineWidth property"
short-title: lineWidth
slug: Web/API/CanvasRenderingContext2D/lineWidth
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.lineWidth
---

{{APIRef("Canvas API")}}

خاصیت **`CanvasRenderingContext2D.lineWidth`** از Canvas 2D API ضخامت خطوط را تنظیم می‌کند.

> [!NOTE]
> خطوط را می‌توان با استفاده از متدهای {{domxref("CanvasRenderingContext2D.stroke()", "stroke()")}}، {{domxref("CanvasRenderingContext2D.strokeRect()", "strokeRect()")}} و {{domxref("CanvasRenderingContext2D.strokeText()", "strokeText()")}} رسم کرد.

## مقدار

یک عدد که ضخامت خط را بر حسب واحدهای فضای مختصات مشخص می‌کند. مقادیر صفر، منفی، {{jsxref("Infinity")}} و {{jsxref("NaN")}} نادیده گرفته می‌شوند. این مقدار به‌طور پیش‌فرض `1.0` است.

## مثال‌ها

### تغییر ضخامت خط

این مثال یک خط و یک مستطیل را با استفاده از ضخامت خط ۱۵ واحد رسم می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.lineWidth = 15;

ctx.beginPath();
ctx.moveTo(20, 20);
ctx.lineTo(130, 130);
ctx.rect(40, 40, 70, 70);
ctx.stroke();
```

#### نتیجه

{{ EmbedLiveSample('Changing_line_width', 700, 180) }}

### مثال‌های بیشتر

برای مثال‌ها و توضیحات بیشتر درباره این خاصیت، به [اعمال سبک‌ها و رنگ‌ها](/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors) در [آموزش Canvas](/en-US/docs/Web/API/Canvas_API/Tutorial) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابطی که این خاصیت را تعریف می‌کند: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.lineCap")}}
- {{domxref("CanvasRenderingContext2D.lineJoin")}}
- [اعمال سبک‌ها و رنگ‌ها](/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors)