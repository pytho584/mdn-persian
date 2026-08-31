---
title: "CanvasRenderingContext2D: createRadialGradient() method"
short-title: createRadialGradient()
slug: Web/API/CanvasRenderingContext2D/createRadialGradient
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.createRadialGradient
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.createRadialGradient()`** در Canvas 2D API با استفاده از اندازه و مختصات دو دایره، یک گرادیان شعاعی ایجاد می‌کند.

این متد یک {{domxref("CanvasGradient")}} برمی‌گرداند. برای اینکه گرادیان روی یک شکل اعمال شود، ابتدا باید به ویژگی‌های {{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle")}} یا {{domxref("CanvasRenderingContext2D.strokeStyle", "strokeStyle")}} اختصاص داده شود.

> [!NOTE]
> مختصات گرادیان سراسری (global) هستند، یعنی نسبت به فضای مختصات فعلی.
> وقتی گرادیان روی یک شکل اعمال می‌شود، مختصات نسبت به مختصات خودِ شکل نیستند.

## سینتکس

```js-nolint
createRadialGradient(x0, y0, r0, x1, y1, r1)
```

متد `createRadialGradient()` با شش پارامتر مشخص می‌شود؛ سه پارامتر دایرهٔ شروع گرادیان و سه پارامتر دایرهٔ پایان آن را تعریف می‌کنند.

### پارامترها

- `x0`
  - : مختصات محور x دایرهٔ شروع.
- `y0`
  - : مختصات محور y دایرهٔ شروع.
- `r0`
  - : شعاع دایرهٔ شروع. باید نامنفی و متناهی باشد.
- `x1`
  - : مختصات محور x دایرهٔ پایان.
- `y1`
  - : مختصات محور y دایرهٔ پایان.
- `r1`
  - : شعاع دایرهٔ پایان. باید نامنفی و متناهی باشد.

### مقدار بازگشتی

یک {{domxref("CanvasGradient")}} شعاعی که با دو دایرهٔ مشخص‌شده مقداردهی اولیه شده است.

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : هنگامی که مقادیر نامتناهی در پارامترها ارسال شوند، پرتاب می‌شود.
- `IndexSizeError` {{domxref("DOMException")}}
  - : هنگامی که شعاع منفی در پارامترها ارسال شود، پرتاب می‌شود.

## مثال‌ها

### پر کردن یک مستطیل با گرادیان شعاعی

در این مثال، یک گرادیان شعاعی با استفاده از متد `createRadialGradient()` مقداردهی اولیه می‌شود. سپس سه ایستگاه رنگی بین دو دایرهٔ گرادیان ایجاد می‌شود. در نهایت گرادیان به بافت بوم (canvas context) اختصاص داده شده و روی یک مستطیل پرشده رندر می‌شود.

#### HTML

```html
<canvas id="canvas" width="200" height="200"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Create a radial gradient
// The inner circle is at x=110, y=90, with radius=30
// The outer circle is at x=100, y=100, with radius=70
const gradient = ctx.createRadialGradient(110, 90, 30, 100, 100, 70);

// Add three color stops
gradient.addColorStop(0, "pink");
gradient.addColorStop(0.9, "white");
gradient.addColorStop(1, "green");

// Set the fill style and draw a rectangle
ctx.fillStyle = gradient;
ctx.fillRect(20, 20, 160, 160);
```

#### نتیجه

{{ EmbedLiveSample('Filling_a_rectangle_with_a_radial_gradient', 700, 240) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کنندهٔ این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.createLinearGradient()")}}
- {{domxref("CanvasRenderingContext2D.createConicGradient()")}}