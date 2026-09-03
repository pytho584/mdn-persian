---
title: "PointerEvent: getPredictedEvents() method"
short-title: getPredictedEvents()
slug: Web/API/PointerEvent/getPredictedEvents
page-type: web-api-instance-method
browser-compat: api.PointerEvent.getPredictedEvents
---

{{APIRef("Pointer Events")}}

متد **`getPredictedEvents()`** متعلق به رابط {{domxref("PointerEvent")}} دنباله‌ای از نمونه‌های `PointerEvent` را بازمی‌گرداند که موقعیت‌های آیندهٔ تخمینی اشاره‌گر را نشان می‌دهند. روش محاسبهٔ این موقعیت‌های پیش‌بینی‌شده به عامل کاربر (user agent) بستگی دارد؛ اما آن‌ها بر اساس نقاط گذشته، سرعت کنونی و مسیر حرکت به دست می‌آیند.

برنامه‌ها می‌توانند از رویدادهای پیش‌بینی‌شده برای «ترسیم پیش‌دستانه» تا یک موقعیت پیش‌بینی‌شده استفاده کنند؛ این کار می‌تواند بسته به تفسیر برنامه از رویدادهای پیش‌بینی‌شده و مورد استفاده، تأخیر درک‌شده را کاهش دهد.

برای تصویری از رویدادهای پیش‌بینی‌شده، به [شکل ۸ در مشخصات](https://w3c.github.io/pointerevents/#figure_predicted) مراجعه کنید.

## نحو

```js-nolint
getPredictedEvents()
```

### پارامترها

هیچ.

### مقدار بازگشتی

دنباله‌ای از نمونه‌های {{domxref('PointerEvent')}}.

### مثال

### HTML

```html
<canvas id="target" width="600" height="300"></canvas>
```

### JavaScript

```js
const canvas = document.getElementById("target");
const ctx = canvas.getContext("2d");

const pointerEvents = [];

function drawCircle(x, y, color) {
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  // draw the last 20 events
  if (pointerEvents.length > 20) {
    pointerEvents.shift();
  }
  pointerEvents.push({ x, y, color });

  for (const pointerEvent of pointerEvents) {
    ctx.beginPath();
    ctx.arc(pointerEvent.x, pointerEvent.y, 10, 0, 2 * Math.PI);
    ctx.strokeStyle = pointerEvent.color;
    ctx.stroke();
  }
}

canvas.addEventListener("pointermove", (e) => {
  // draw a circle for the current event
  drawCircle(e.clientX, e.clientY, "black");

  const predictedEvents = e.getPredictedEvents();
  for (let predictedEvent of predictedEvents) {
    // give it an offset so we can see the difference and color it red
    drawCircle(predictedEvent.clientX + 20, predictedEvent.clientY + 20, "red");
  }
});
```

### نتیجه

{{EmbedLiveSample("Example", "", "320")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}