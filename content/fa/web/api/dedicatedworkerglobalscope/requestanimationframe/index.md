---
title: "DedicatedWorkerGlobalScope: requestAnimationFrame() method"
short-title: requestAnimationFrame()
slug: Web/API/DedicatedWorkerGlobalScope/requestAnimationFrame
page-type: web-api-instance-method
browser-compat: api.DedicatedWorkerGlobalScope.requestAnimationFrame
---

{{APIRef("Web Workers API")}}{{AvailableInWorkers("dedicated")}}

متد **`requestAnimationFrame()`** در رابط {{domxref("DedicatedWorkerGlobalScope")}} به مرورگر اعلام می‌کند که شما می‌خواهید یک درخواست فریم انیمیشن انجام دهید و یک تابع callback که توسط کاربر ارائه شده است را قبل از بازنقاشی بعدی فراخوانی کنید.

فرکانس فراخوانی تابع callback معمولاً با نرخ تازه‌سازی نمایشگر مطابقت دارد. رایج‌ترین نرخ تازه‌سازی ۶۰ هرتز (۶۰ چرخه/فریم در ثانیه) است، اگرچه ۷۵ هرتز، ۱۲۰ هرتز و ۱۴۴ هرتز نیز به طور گسترده استفاده می‌شوند. فراخوانی‌های `requestAnimationFrame()` در بیشتر مرورگرها هنگام اجرا در برگه‌های پس‌زمینه یا {{HTMLElement("iframe")}}های مخفی متوقف می‌شوند تا عملکرد و عمر باتری بهبود یابد.

یک فراخوانی به متد `requestAnimationFrame()` فقط یک فراخوانی واحد به تابع callback زمان‌بندی می‌کند. اگر می‌خواهید فریم دیگری را انیمیشن کنید، تابع callback شما باید دوباره `requestAnimationFrame()` را فراخوانی کند.

> [!WARNING]
> حتماً همیشه از اولین آرگومان (یا روش دیگری برای دریافت زمان فعلی) برای محاسبه میزان پیشرفت انیمیشن در یک فریم استفاده کنید — **در غیر این صورت، انیمیشن در صفحه‌نمایش‌های با نرخ تازه‌سازی بالا سریع‌تر اجرا خواهد شد**. برای راه‌های انجام این کار، نمونه‌های زیر را ببینید.

فراخوانی متد `requestAnimationFrame()` نیاز دارد که worker فعلی دارای یک {{domxref("Window", "window")}} مالک مرتبط باشد. یعنی worker فعلی باید توسط {{domxref("Window", "window")}} یا توسط یک dedicated worker که خود دارای یک {{domxref("Window", "window")}} مالک مرتبط است، ایجاد شده باشد.

## Syntax

```js-nolint
requestAnimationFrame(callback)
```

### Parameters

- `callback`
  - : تابعی که وقتی زمان به‌روزرسانی انیمیشن شما برای بازنقاشی بعدی فرا رسید، فراخوانی می‌شود. این تابع callback یک آرگومان دریافت می‌کند:
    - `timestamp`
      - : یک {{domxref("DOMHighResTimeStamp")}} که زمان پایان رندرینگ فریم قبلی را نشان می‌دهد (بر اساس تعداد میلی‌ثانیه از [مبدأ زمان](/en-US/docs/Web/API/Performance/timeOrigin)). این timestamp یک عدد اعشاری بر حسب میلی‌ثانیه است، اما با حداقل دقت ۱ میلی‌ثانیه. مقدار timestamp همچنین مشابه فراخوانی {{domxref('performance.now()')}} در شروع تابع callback است، اما هرگز مقدار یکسانی نیست.
        وقتی چندین callback که توسط `requestAnimationFrame()` در صف قرار گرفته‌اند در یک فریم شروع به اجرا می‌کنند، هر کدام timestamp یکسانی دریافت می‌کنند، حتی اگر در حین محاسبه workload هر callback قبلی، زمان گذشته باشد.

### Return value

یک مقدار عدد صحیح `long` که شناسه درخواست است و به طور یکتا ورودی در لیست callback را مشخص می‌کند. این یک مقدار غیر صفر است، اما نمی‌توانید فرض دیگری درباره آن داشته باشید. می‌توانید این مقدار را به {{domxref("DedicatedWorkerGlobalScope.cancelAnimationFrame()", "cancelAnimationFrame()")}} ارسال کنید تا درخواست callback تازه‌سازی لغو شود، عمل لغو باید در همان worker انجام شده باشد.

### Exceptions

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر متد توسط worker فعلی پشتیبانی نشود، پرتاب می‌شود.

## Examples

در اینجا یک مثال کامل آورده شده است که نحوه استفاده از `requestAnimationFrame()` در یک dedicated worker با `OffscreenCanvas` را نشان می‌دهد.

HTML باید شامل موارد زیر باشد:

```html
<canvas width="100" height="100"></canvas>
```

باید به JavaScript زیر متصل شود:

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

در نخ اصلی، ما با انتقال کنترل یک عنصر {{HTMLElement("canvas")}} به یک {{domxref("OffscreenCanvas")}} با استفاده از {{domxref("HTMLCanvasElement.transferControlToOffscreen()")}} شروع می‌کنیم و یک پیام برای شروع کار به worker ارسال می‌کنیم، همراه با canvas offscreen.

در فایل worker (`worker.js`)، منطق انیمیشن را مدیریت می‌کنیم. هنگام دریافت پیام `"start"`، worker انیمیشن را شروع می‌کند و مستطیل را از چپ به راست حرکت می‌دهد. هنگام دریافت پیام `"stop"`، انیمیشن را متوقف می‌کند.

در نهایت، نخ اصلی می‌تواند یک پیام `"stop"` به worker ارسال کند تا پس از یک تأخیر انیمیشن متوقف شود و اجازه دهد انیمیشن قبل از توقف قابل مشاهده باشد.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("DedicatedWorkerGlobalScope.cancelAnimationFrame()")}}
- {{domxref("Window.requestAnimationFrame()")}}