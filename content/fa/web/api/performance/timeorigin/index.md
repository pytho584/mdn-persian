---
title: "Performance: timeOrigin property"
short-title: timeOrigin
slug: Web/API/Performance/timeOrigin
page-type: web-api-instance-property
browser-compat: api.Performance.timeOrigin
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`timeOrigin`** از رابط {{domxref("Performance")}}، یک زمان‌سنج با وضوح بالا (high resolution timestamp) را بازمی‌گرداند که به عنوان پایه‌ای برای زمان‌سنج‌های مرتبط با عملکرد استفاده می‌شود.

در زمینه‌های Window، این مقدار نشان‌دهنده زمانی است که ناوبری (navigation) آغاز شده است. در زمینه‌های {{domxref("Worker")}} و {{domxref("ServiceWorker")}}، این مقدار نشان‌دهنده زمانی است که worker اجرا می‌شود. می‌توانید از این ویژگی برای همگام‌سازی مبدأهای زمانی بین زمینه‌های مختلف استفاده کنید (مثال زیر را ببینید).

> [!NOTE]
> مقدار `performance.timeOrigin` ممکن است با مقدار بازگردانده‌شده توسط {{jsxref("Date.now()")}} که در مبدأ زمانی اجرا شده است متفاوت باشد، زیرا `Date.now()` ممکن است تحت تأثیر تنظیمات سیستم و کاربر، انحراف ساعت (clock skew) و موارد دیگر قرار گیرد. ویژگی `timeOrigin` یک [ساعت یکنواخت (monotonic clock)](https://w3c.github.io/hr-time/#dfn-monotonic-clock) است که زمان فعلی آن هرگز کاهش نمی‌یابد و تحت تأثیر این تنظیمات قرار نمی‌گیرد.

## مقدار

یک زمان‌سنج با وضوح بالا که به عنوان آغاز طول عمر سند جاری در نظر گرفته می‌شود. به صورت زیر محاسبه می‌شود:

- اگر {{Glossary("global object","شیء سراسری")}} اسکریپت یک {{domxref("Window")}} باشد، مبدأ زمانی به صورت زیر تعیین می‌شود:
  - اگر {{domxref("Document")}} جاری اولین سندی است که در `Window` بارگذاری شده است، مبدأ زمانی زمانی است که زمینه مرورگر (browser context) ایجاد شده است.
  - اگر در فرآیند تخلیه (unloading) سند قبلی که در پنجره بارگذاری شده بود، یک کادر تأیید (confirmation dialog) برای دریافت تأیید کاربر برای ترک صفحه قبلی نمایش داده شده باشد، مبدأ زمانی زمانی است که کاربر تأیید کرده است که ناوبری به صفحه جدید قابل قبول است.
  - اگر هیچ‌یک از موارد بالا مبدأ زمانی را تعیین نکند، آنگاه مبدأ زمانی زمانی است که ناوبری مسئول ایجاد `Document` جاری پنجره انجام شده است.

- اگر شیء سراسری اسکریپت یک {{domxref("WorkerGlobalScope")}} باشد (یعنی اسکریپت به عنوان یک web worker اجرا می‌شود)، مبدأ زمانی لحظه‌ای است که worker ایجاد شده است.
- در سایر موارد، مبدأ زمانی تعریف‌نشده (undefined) است.

## مثال‌ها

### همگام‌سازی زمان بین زمینه‌ها

برای در نظر گرفتن مبدأهای زمانی متفاوت در زمینه‌های window و worker، می‌توانید با کمک ویژگی `timeOrigin`، زمان‌سنج‌های دریافتی از اسکریپت‌های worker را ترجمه کنید تا زمان‌بندی‌ها برای کل برنامه همگام شوند.

در worker.js

```js
self.addEventListener("connect", (event) => {
  const port = event.ports[0];

  port.onmessage = (event) => {
    const workerTaskStart = performance.now();
    // doSomeWork()
    const workerTaskEnd = performance.now();
  };

  // Convert worker-relative timestamps to absolute timestamps, then send to the window
  port.postMessage({
    startTime: workerTaskStart + performance.timeOrigin,
    endTime: workerTaskEnd + performance.timeOrigin,
  });
});
```

در main.js

```js
const worker = new SharedWorker("worker.js");
worker.port.addEventListener("message", (event) => {
  // Convert absolute timestamps into window-relative timestamps
  const workerTaskStart = event.data.startTime - performance.timeOrigin;
  const workerTaskEnd = event.data.endTime - performance.timeOrigin;

  console.log("Worker task start: ", workerTaskStart);
  console.log("Worker task end: ", workerTaskEnd);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}