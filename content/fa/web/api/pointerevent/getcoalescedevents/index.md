---
title: "PointerEvent: getCoalescedEvents() method"
short-title: getCoalescedEvents()
slug: Web/API/PointerEvent/getCoalescedEvents
page-type: web-api-instance-method
browser-compat: api.PointerEvent.getCoalescedEvents
---

{{APIRef("Pointer Events")}} {{secureContext_header}}

متد **`getCoalescedEvents()`** در رابط (interface) {{domxref("PointerEvent")}} دنباله‌ای از نمونه‌های `PointerEvent` را برمی‌گرداند که در یک رویداد {{domxref('Element/pointermove_event', 'pointermove')}} یا {{domxref('Element/pointerrawupdate_event', 'pointerrawupdate')}} ادغام (coalesce) شده‌اند. عامل کاربر (user agent) به جای ایجاد جریانی از رویدادهای متعدد {{domxref('Element/pointermove_event', 'pointermove')}}، چندین به‌روزرسانی را در قالب یک رویداد واحد ترکیب می‌کند. این کار به بهبود کارایی کمک می‌کند، زیرا عامل کاربر باید رویدادهای کمتری را پردازش کند؛ اما در عوض، میزان جزئیات و دقت ردیابی، به‌ویژه در حرکت‌های سریع و با دامنه بزرگ، کاهش می‌یابد.

متد **`getCoalescedEvents()`** به برنامه‌ها امکان می‌دهد در صورت نیاز به تمام تغییرات موقعیتِ ادغام‌نشده دسترسی داشته باشند تا داده‌های حرکت اشاره‌گر با دقت پردازش شوند. برای نمونه، تغییرات موقعیت ادغام‌نشده در برنامه‌های نقاشی مطلوب هستند؛ زیرا دسترسی به همه رویدادها به ایجاد منحنی‌های نرم‌تری کمک می‌کند که با حرکت واقعی اشاره‌گر هماهنگی بهتری دارند.

برای مشاهده تصویری از رویدادهای ادغام‌شده، به [شکل ۷ در مشخصات](https://w3c.github.io/pointerevents/#figure_coalesced) مراجعه کنید.

## نحو

```js-nolint
getCoalescedEvents()
```

### پارامترها

هیچ.

### مقدار بازگشتی

دنباله‌ای از نمونه‌های {{domxref('PointerEvent')}}.

## مثال

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

  const coalescedEvents = e.getCoalescedEvents();
  for (let coalescedEvent of coalescedEvents) {
    // give it an offset so we can see the difference and color it red
    drawCircle(coalescedEvent.clientX + 20, coalescedEvent.clientY + 20, "red");
  }
});
```

### نتیجه

{{EmbedLiveSample("Example", "", "320")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}