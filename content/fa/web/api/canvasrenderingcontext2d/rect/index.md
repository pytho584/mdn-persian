---
title: "CanvasRenderingContext2D: rect() method"
---

---
title: "CanvasRenderingContext2D: rect() method"
short-title: rect()
slug: Web/API/CanvasRenderingContext2D/rect
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.rect
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.rect()`** در Canvas 2D API، یک مستطیل به مسیر جاری اضافه می‌کند.

این متد مانند سایر روش‌هایی که مسیر جاری را تغییر می‌دهند، مستقیماً چیزی را رندر نمی‌کند. برای رسم مستطیل روی بوم، می‌توانید از متدهای {{domxref("CanvasRenderingContext2D.fill", "fill()")}} یا {{domxref("CanvasRenderingContext2D.stroke", "stroke()")}} استفاده کنید.

> [!NOTE]
> برای ایجاد و رندر یک مستطیل در یک مرحله، از متدهای {{domxref("CanvasRenderingContext2D.fillRect", "fillRect()")}} یا {{domxref("CanvasRenderingContext2D.strokeRect", "strokeRect()")}} استفاده کنید.

## سینتکس

```js-nolint
rect(x, y, width, height)
```

متد `rect()` یک مسیر مستطیلی ایجاد می‌کند که نقطه شروع آن در `(x, y)` است و اندازه آن توسط `width` و `height` مشخص می‌شود.

### پارامترها

- `x`
  - : مختصات محور x نقطه شروع مستطیل.
- `y`
  - : مختصات محور y نقطه شروع مستطیل.
- `width`
  - : عرض مستطیل. مقادیر مثبت به سمت راست و مقادیر منفی به سمت چپ هستند.
- `height`
  - : ارتفاع مستطیل. مقادیر مثبت به سمت پایین و مقادیر منفی به سمت بالا هستند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### رسم یک مستطیل

این مثال یک مسیر مستطیلی را با استفاده از متد `rect()` ایجاد می‌کند. سپس مسیر با استفاده از متد `fill()` رندر می‌شود.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### جاوااسکریپت

گوشه مستطیل در مختصات (10, 20) قرار دارد. عرض آن 150 و ارتفاع آن 100 است.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.beginPath(); // Start a new path
ctx.rect(10, 20, 150, 100); // Add a rectangle to the current path
ctx.fill(); // Render the path
```

#### نتیجه

{{ EmbedLiveSample('Drawing_a_rectangle', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.fillRect")}}
- {{domxref("CanvasRenderingContext2D.strokeRect()")}}
- {{domxref("CanvasRenderingContext2D.fill()")}}
- {{domxref("CanvasRenderingContext2D.stroke()")}}