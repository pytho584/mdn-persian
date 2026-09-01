---
title: "DedicatedWorkerGlobalScope: cancelAnimationFrame() method"
short-title: cancelAnimationFrame()
slug: Web/API/DedicatedWorkerGlobalScope/cancelAnimationFrame
page-type: web-api-instance-method
browser-compat: api.DedicatedWorkerGlobalScope.cancelAnimationFrame
---

{{APIRef("Web Workers API")}}{{AvailableInWorkers("dedicated")}}

متد **`cancelAnimationFrame()`** از رابط {{domxref("DedicatedWorkerGlobalScope")}} درخواست فریم انیمیشنی را که پیش‌تر از طریق فراخوانی {{domxref("DedicatedWorkerGlobalScope.requestAnimationFrame()", "requestAnimationFrame()")}} زمان‌بندی شده بود، لغو می‌کند.

فراخوانی متد `cancelAnimationFrame()` مستلزم آن است که worker کنونی یک {{domxref("Window", "window")}} مالک مرتبط داشته باشد. این بدان معناست که worker کنونی باید توسط {{domxref("Window", "window")}} یا توسط یک dedicated worker ساخته شده باشد که آن نیز یک {{domxref("Window", "window")}} مالک مرتبط دارد.

## سینتکس

```js-nolint
cancelAnimationFrame(handle)
```

### پارامترها

- `handle`
  - : مقدار ID که توسط یک فراخوانی به {{domxref("DedicatedWorkerGlobalScope.requestAnimationFrame()", "requestAnimationFrame()")}} بازگردانده شده است؛ این فراخوانی باید در همان worker انجام شده باشد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر این متد توسط worker کنونی پشتیبانی نشود، پرتاب می‌شود.

## مثال‌ها

در ادامه یک مثال کامل آورده شده است که نحوه استفاده از `requestAnimationFrame()` در یک dedicated worker با `OffscreenCanvas` را نشان می‌دهد.

HTML باید شامل موارد زیر باشد:

```html
<canvas width="100" height="100"></canvas>
```

باید به جاوااسکریپت زیر متصل شود:

```js
const worker = new Worker("worker.js");

// Transfer canvas control to the worker
const offscreenCanvas = document
  .querySelector("canvas")
  .transferControlToOffscreen();

// Start the animation
worker.postMessage(
  {
    type: "start",
    canvas: offscreenCanvas,
  },
  [offscreenCanvas],
);

// Stop the animation after 5 seconds
setTimeout(() => {
  worker.postMessage({
    type: "stop",
  });
}, 5000);
```

**worker.js:**

```js
let ctx;
let pos = 0;
let animationId;
let isRunning = false;
let lastTime = 0;

function draw(currentTime) {
  if (!isRunning) return;

  // Calculate delta time for smooth animation
  if (lastTime === 0) lastTime = currentTime;
  const deltaTime = (currentTime - lastTime) / 1000;
  lastTime = currentTime;

  // Clear and draw the moving rectangle
  ctx.clearRect(0, 0, 100, 100);
  ctx.fillRect(pos, 0, 10, 10);
  pos += 50 * deltaTime; // Move 50 pixels per second

  // Loop the animation
  if (pos > 100) pos = -10;

  animationId = self.requestAnimationFrame(draw);
}

self.addEventListener("message", (e) => {
  if (e.data.type === "start") {
    const transferredCanvas = e.data.canvas;
    ctx = transferredCanvas.getContext("2d");
    isRunning = true;
    lastTime = 0;
    animationId = self.requestAnimationFrame(draw);
  }
  if (e.data.type === "stop") {
    isRunning = false;
    if (animationId) {
      self.cancelAnimationFrame(animationId);
    }
  }
});
```

در نخ اصلی، ابتدا کنترل یک عنصر {{HTMLElement("canvas")}} را با استفاده از {{domxref("HTMLCanvasElement.transferControlToOffscreen()")}} به یک {{domxref("OffscreenCanvas")}} منتقل می‌کنیم و پیامی با `"start"` و همراه با offscreen canvas برای شروع کار به worker ارسال می‌کنیم.

در فایل worker (یعنی `worker.js`)، منطق انیمیشن را مدیریت می‌کنیم. هنگام دریافت پیام `"start"`، worker انیمیشن را شروع می‌کند و مستطیل را از چپ به راست حرکت می‌دهد. پس از دریافت پیام `"stop"`، انیمیشن متوقف می‌شود.

در نهایت، نخ اصلی می‌تواند پس از یک تأخیر، پیام `"stop"` را به worker ارسال کند تا انیمیشن متوقف شود و این امکان فراهم شود که انیمیشن پیش از توقف دیده شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DedicatedWorkerGlobalScope.requestAnimationFrame()")}}
- {{domxref("Window.cancelAnimationFrame()")}}