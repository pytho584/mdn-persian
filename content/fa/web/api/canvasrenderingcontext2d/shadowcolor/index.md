---
title: "CanvasRenderingContext2D: shadowColor property"
short-title: shadowColor
slug: Web/API/CanvasRenderingContext2D/shadowColor
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.shadowColor
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.shadowColor`** از Canvas 2D API، رنگ سایه‌ها را مشخص می‌کند.

توجه داشته باشید که شفافیتِ رندرِ سایه، هنگام fill کردن تحت تأثیر شفافیت رنگ {{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle")}} و هنگام stroke کردن تحت تأثیر شفافیت رنگ {{domxref("CanvasRenderingContext2D.strokeStyle", "strokeStyle")}} قرار می‌گیرد.

> [!NOTE]
> سایه‌ها فقط زمانی رسم می‌شوند که ویژگی `shadowColor` روی یک مقدار غیر شفاف تنظیم شده باشد. علاوه بر آن، یکی از ویژگی‌های {{domxref("CanvasRenderingContext2D.shadowBlur", "shadowBlur")}}، {{domxref("CanvasRenderingContext2D.shadowOffsetX", "shadowOffsetX")}} یا {{domxref("CanvasRenderingContext2D.shadowOffsetY", "shadowOffsetY")}} باید غیر صفر باشد.

## مقدار

یک رشته که به‌عنوان یک مقدار [CSS](/en-US/docs/Web/CSS) {{cssxref("&lt;color&gt;")}} تجزیه می‌شود. مقدار پیش‌فرض، سیاهِ کاملاً شفاف است.

## مثال‌ها

### افزودن سایه به شکل‌ها

این مثال به دو مربع سایه اضافه می‌کند؛ مربع اول با fill رسم می‌شود و مربع دوم با stroke. ویژگی `shadowColor` رنگ سایه‌ها را تنظیم می‌کند، در حالی که `shadowOffsetX` و `shadowOffsetY` موقعیت آن‌ها را نسبت به شکل‌ها تعیین می‌کنند.

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
ctx.shadowOffsetX = 10;
ctx.shadowOffsetY = 10;

// Filled rectangle
ctx.fillRect(20, 20, 100, 100);

// Stroked rectangle
ctx.lineWidth = 6;
ctx.strokeRect(170, 20, 100, 100);
```

#### نتیجه

{{ EmbedLiveSample('Adding_a_shadow_to_shapes', 700, 180) }}

### سایه‌ها روی شکل‌های نیمه‌شفاف

شفافیت یک سایه تحت تأثیر میزان شفافیت شیءِ والد آن قرار می‌گیرد (حتی وقتی `shadowColor` یک مقدار کاملاً مات را مشخص کند). این مثال یک مستطیل را با رنگ‌های نیمه‌شفاف stroke و fill می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

مقدار آلفای حاصل برای سایهٔ fill برابر با `.8 * .2`، یعنی `.16` است. آلفای سایهٔ stroke برابر با `.8 * .6`، یعنی `.48` است.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Shadow
ctx.shadowColor = "rgb(255 0 0 / 80%)";
ctx.shadowBlur = 8;
ctx.shadowOffsetX = 30;
ctx.shadowOffsetY = 20;

// Filled rectangle
ctx.fillStyle = "rgb(0 255 0 / 20%)";
ctx.fillRect(10, 10, 150, 100);

// Stroked rectangle
ctx.lineWidth = 10;
ctx.strokeStyle = "rgb(0 0 255 / 60%)";
ctx.strokeRect(10, 10, 150, 100);
```

#### نتیجه

{{ EmbedLiveSample('Shadows_on_translucent_shapes', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

### یادداشت‌های ویژهٔ WebKit/Blink

در مرورگرهای مبتنی بر WebKit و Blink، متد غیراستاندارد و منسوخ `ctx.setShadow()` علاوه بر این ویژگی پیاده‌سازی شده است.

```js
setShadow(width, height, blur, color, alpha);
setShadow(width, height, blur, graylevel, alpha);
setShadow(width, height, blur, r, g, b, a);
setShadow(width, height, blur, c, m, y, k, a);
```

## همچنین ببینید

- رابطی که این ویژگی را تعریف می‌کند: {{domxref("CanvasRenderingContext2D")}}