---
title: "CanvasRenderingContext2D: strokeRect() method"
short-title: strokeRect()
slug: Web/API/CanvasRenderingContext2D/strokeRect
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.strokeRect
---

{{APIRef("Canvas API")}}

متد
**`CanvasRenderingContext2D.strokeRect()`**
از API بوم‌نقاشی (Canvas 2D) مستطیلی را رسم می‌کند که بر اساس
{{domxref("CanvasRenderingContext2D.strokeStyle", "strokeStyle")}} و سایر تنظیمات زمینه،
فقط خطِ دور آن (طرح کلی) ترسیم می‌شود.

این متد مستقیماً روی بوم نقاشی می‌کشد و مسیر فعلی را تغییر نمی‌دهد، بنابراین
تماس‌های بعدی با {{domxref("CanvasRenderingContext2D.fill()", "fill()")}} یا
{{domxref("CanvasRenderingContext2D.stroke()", "stroke()")}} هیچ تأثیری روی آن نخواهند داشت.

## نحو (Syntax)

```js-nolint
strokeRect(x, y, width, height)
```

متد `strokeRect()` یک مستطیل خط‌دورکشیده رسم می‌کند که نقطهٔ شروع آن
در `(x, y)` است و اندازهٔ آن توسط `width` و `height` مشخص می‌شود.

### پارامترها

- `x`
  - : مختصات محور x نقطهٔ شروع مستطیل.
- `y`
  - : مختصات محور y نقطهٔ شروع مستطیل.
- `width`
  - : عرض مستطیل. مقادیر مثبت به سمت راست و مقادیر منفی به سمت چپ هستند.
- `height`
  - : ارتفاع مستطیل. مقادیر مثبت به سمت پایین و مقادیر منفی به سمت بالا هستند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

### یک مستطیل خط‌دورکشیده ساده

این مثال یک مستطیل با خط دور سبز را با استفاده از متد `strokeRect()` رسم می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

گوشهٔ بالا-چپ مستطیل در (20, 10) قرار دارد. عرض آن 160 و ارتفاع آن 100 است.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.strokeStyle = "green";
ctx.strokeRect(20, 10, 160, 100);
```

#### نتیجه

{{ EmbedLiveSample('A_simple_stroked_rectangle', 700, 180) }}

### اعمال تنظیمات مختلف زمینه

این مثال مستطیلی را با سایهٔ افتاده و خطوط دور ضخیم و پخ‌دار رسم می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.shadowColor = "#dd5533";
ctx.shadowBlur = 20;
ctx.lineJoin = "bevel";
ctx.lineWidth = 15;
ctx.strokeStyle = "#3388ff";
ctx.strokeRect(30, 30, 160, 90);
```

#### نتیجه

{{ EmbedLiveSample('Applying_various_context_settings', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کنندهٔ این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.strokeStyle")}}
- {{domxref("CanvasRenderingContext2D.clearRect()")}}
- {{domxref("CanvasRenderingContext2D.fillRect()")}}