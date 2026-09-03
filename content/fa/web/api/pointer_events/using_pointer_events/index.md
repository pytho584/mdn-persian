---
title: Using Pointer Events
slug: Web/API/Pointer_events/Using_Pointer_Events
page-type: guide
browser-compat: api.PointerEvent
---

{{DefaultAPISidebar("Pointer Events")}}

این راهنما نحوهٔ استفاده از [رویدادهای اشاره‌گر](/en-US/docs/Web/API/Pointer_events) و عنصر HTML {{HTMLElement("canvas")}} را برای ساخت یک برنامهٔ نقاشی با پشتیبانی از لمسِ چندگانه نشان می‌دهد. این مثال بر پایهٔ [مرور رویدادهای لمسی](/en-US/docs/Web/API/Touch_events) است، با این تفاوت که از مدل رویدادِ ورودیِ {{domxref("PointerEvent","pointer events", "", 1)}} استفاده می‌کند. تفاوت دیگر این است که چون رویدادهای اشاره‌گر مستقل از دستگاه اشاره‌گر هستند، برنامه با همان کد، ورودی‌های مختصاتی را از ماوس، قلم یا نوک انگشت می‌پذیرد.

این برنامه فقط در مرورگری کار می‌کند که از رویدادهای اشاره‌گر پشتیبانی کند.

## تعاریف

- سطح
  - : سطحی حساس به لمس. این سطح می‌تواند یک ترک‌پد، یک صفحه‌نمایش لمسی، یا حتی نگاشت مجازی سطح میز کاربر (یا زیرِ ماوس) نسبت به صفحهٔ فیزیکی باشد.
- نقطهٔ لمس
  - : نقطه‌ای از تماس با سطح. این نقطه می‌تواند یک انگشت (یا آرنج، گوش، بینی و مانند آن، اما معمولاً انگشت)، قلم، ماوس، یا هر روش دیگری برای تعیین یک نقطهٔ واحد روی سطح باشد.

## مثال‌ها

> [!NOTE]
> متن زیر هنگام توصیف تماس با سطح از واژهٔ «انگشت» استفاده می‌کند، اما البته ممکن است این تماس یک قلم، ماوس، یا روش دیگری برای اشاره به یک نقطه باشد.

### برنامهٔ نقاشی

#### HTML

اچ‌تی‌ام‌ال فقط شامل یک عنصر {{HTMLElement("canvas")}} است. منحنی‌ها در پاسخ به ژست‌های لمسی کاربر رسم می‌شوند. همچنین یک دکمه برای پاک کردن بوم اضافه شده است.

```html
<canvas id="canvas" width="600" height="600">
  Your browser does not support the canvas element.
</canvas>
<button id="clear">Clear canvas</button>
```

#### CSS

خاصیت {{cssxref("touch-action")}} روی `none` تنظیم شده است تا مرورگر رفتار پیش‌فرض لمس را روی این برنامه اعمال نکند.

```css
#canvas {
  border: solid black 1px;
  touch-action: none;
  display: block;
}
```

#### JavaScript

ما همهٔ لمس‌های در جریان را پیگیری می‌کنیم و برای هرکدام خط‌هایی رسم می‌کنیم. از `colors` برای تمایز بین انگشت‌های مختلف استفاده می‌شود.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Mapping from the pointerId to the current finger position
const ongoingTouches = new Map();
const colors = ["red", "green", "blue"];
```

تابع `handleStart` به رویداد {{domxref("Element/pointerdown_event", "pointerdown")}} گوش می‌دهد و در شروع لمس یک دایره رسم می‌کند.

```js
function handleStart(event) {
  const touch = {
    pageX: event.pageX,
    pageY: event.pageY,
    color: colors[ongoingTouches.size % colors.length],
  };
  ongoingTouches.set(event.pointerId, touch);

  ctx.beginPath();
  ctx.arc(touch.pageX, touch.pageY, 4, 0, 2 * Math.PI, false);
  ctx.fillStyle = touch.color;
  ctx.fill();
}

canvas.addEventListener("pointerdown", handleStart);
```

تابع `handleEnd` به رویداد {{domxref("Element/pointerup_event", "pointerup")}} گوش می‌دهد و در پایان لمس یک مربع رسم می‌کند.

```js
function handleEnd(event) {
  const touch = ongoingTouches.get(event.pointerId);

  if (!touch) {
    console.error(`End: Could not find touch ${event.pointerId}`);
    return;
  }

  ctx.lineWidth = 4;
  ctx.fillStyle = touch.color;
  ctx.beginPath();
  ctx.moveTo(touch.pageX, touch.pageY);
  ctx.lineTo(event.pageX, event.pageY);
  ctx.fillRect(event.pageX - 4, event.pageY - 4, 8, 8);
  ongoingTouches.delete(event.pointerId);
}

canvas.addEventListener("pointerup", handleEnd);
```

تابع `handleCancel` به رویداد {{domxref("Element/pointercancel_event", "pointercancel")}} گوش می‌دهد و پیگیری لمس را متوقف می‌کند.

```js
function handleCancel(event) {
  const touch = ongoingTouches.get(event.pointerId);

  if (!touch) {
    console.error(`Cancel: Could not find touch ${event.pointerId}`);
    return;
  }

  ongoingTouches.delete(event.pointerId);
}

canvas.addEventListener("pointercancel", handleCancel);
```

تابع `handleMove` به رویداد {{domxref("Element/pointermove_event", "pointermove")}} گوش می‌دهد و خطی بین ابتدا و انتهای لمس رسم می‌کند.

```js
function handleMove(event) {
  const touch = ongoingTouches.get(event.pointerId);

  // Event was not started
  if (!touch) {
    return;
  }

  ctx.beginPath();
  ctx.moveTo(touch.pageX, touch.pageY);
  ctx.lineTo(event.pageX, event.pageY);
  ctx.lineWidth = 4;
  ctx.strokeStyle = touch.color;
  ctx.stroke();

  const newTouch = {
    pageX: event.pageX,
    pageY: event.pageY,
    color: touch.color,
  };

  ongoingTouches.set(event.pointerId, newTouch);
}

canvas.addEventListener("pointermove", handleMove);
```

در پایان، قابلیت پاک‌کردن بوم را اضافه می‌کنیم.

```js
document.getElementById("clear").addEventListener("click", () => {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
});
```

{{EmbedLiveSample("drawing_application", "", "700")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [رویدادهای اشاره‌گر](/en-US/docs/Web/API/Pointer_events)
- [رویدادهای لمسی](/en-US/docs/Web/API/Touch_events)