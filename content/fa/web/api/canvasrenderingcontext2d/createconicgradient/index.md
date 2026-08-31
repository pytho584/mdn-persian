---
title: "CanvasRenderingContext2D: createConicGradient() method"
short-title: createConicGradient()
slug: Web/API/CanvasRenderingContext2D/createConicGradient
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.createConicGradient
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.createConicGradient()`** متعلق به Canvas 2D API، یک گرادیان دور یک نقطه با مختصات مشخص ایجاد می‌کند.

این متد یک {{domxref("CanvasGradient")}} مخروطی برمی‌گرداند. برای اعمال به یک شکل، ابتدا باید گرادیان به ویژگی‌های {{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle")}} یا {{domxref("CanvasRenderingContext2D.strokeStyle", "strokeStyle")}} اختصاص داده شود.

> [!NOTE]
> مختصات گرادیان سراسری هستند، یعنی نسبت به فضای مختصات فعلی سنجیده می‌شوند. وقتی روی یک شکل اعمال می‌شود، مختصات نسبت به مختصات خودِ شکل **نیستند**.

## نحو

```js-nolint
createConicGradient(startAngle, x, y)
```

### پارامترها

- `startAngle`
  - : زاویه‌ای که گرادیان از آن شروع می‌شود، بر حسب رادیان. زاویه از خطی که از مرکز به سمت راست به صورت افقی می‌رود آغاز شده و در جهت عقربه‌های ساعت ادامه می‌یابد.
- `x`
  - : مختصات محور x مرکز گرادیان.
- `y`
  - : مختصات محور y مرکز گرادیان.

### مقدار بازگشتی

یک {{domxref("CanvasGradient")}} مخروطی.

## مثال‌ها

### پر کردن یک مستطیل با گرادیان مخروطی

این مثال با استفاده از متد `createConicGradient()` یک گرادیان مخروطی مقداردهی می‌کند. سپس پنج ایستگاه رنگی (color stop) در اطراف مختصات مرکز ایجاد می‌شود. در نهایت، گرادیان به بافت بوم (canvas context) اختصاص داده شده و روی یک مستطیل پر شده رندر می‌شود.

#### HTML

```html
<canvas id="canvas" width="240" height="240"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Create a conic gradient
// The start angle is 0
// The center position is 100, 100
const gradient = ctx.createConicGradient(0, 100, 100);

// Add five color stops
gradient.addColorStop(0, "red");
gradient.addColorStop(0.25, "orange");
gradient.addColorStop(0.5, "yellow");
gradient.addColorStop(0.75, "green");
gradient.addColorStop(1, "blue");

// Set the fill style and draw a rectangle
ctx.fillStyle = gradient;
ctx.fillRect(20, 20, 200, 200);
```

#### نتیجه مستطیل

{{ EmbedLiveSample('Filling_a_rectangle_with_a_conic_gradient', 240, 240) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasGradient")}}
- {{domxref("CanvasRenderingContext2D.createLinearGradient()")}}
- {{domxref("CanvasRenderingContext2D.createRadialGradient()")}}