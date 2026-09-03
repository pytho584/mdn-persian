---
title: "PerformanceResourceTiming: workerStart property"
short-title: workerStart
slug: Web/API/PerformanceResourceTiming/workerStart
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.workerStart
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`workerStart`** از رابط {{domxref("PerformanceResourceTiming")}} یک {{domxref("DOMHighResTimeStamp")}} را بلافاصله قبل از ارسال {{domxref("FetchEvent")}} برمی‌گرداند، اگر یک Service Worker از قبل در حال اجرا باشد، یا بلافاصله قبل از شروع‌کردن رشتهٔ Service Worker، اگر هنوز در حال اجرا نباشد. اگر منبع توسط یک Service Worker رهگیری نشده باشد، این ویژگی همیشه `0` برمی‌گرداند.

## مقدار

ویژگی `workerStart` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp")}}.
- در صورت عدم استفاده از سرویس‌کارگر، مقدار `0`.
- اگر منبع یک درخواست متقاطع (cross-origin) باشد و از هدر پاسخ {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد، مقدار `0`.

## مثال‌ها

### اندازه‌گیری زمان پردازش ServiceWorker

از ویژگی‌های `workerStart` و {{domxref("PerformanceResourceTiming.fetchStart", "fetchStart")}} می‌توان برای اندازه‌گیری زمان پردازش یک {{domxref("ServiceWorker")}} استفاده کرد.

```js
const workerProcessingTime = entry.fetchStart - entry.workerStart;
```

مثال استفاده از {{domxref("PerformanceObserver")}} که با ثبت هر ورودی `resource` جدید در خط زمانی عملکرد مرورگر، اطلاع می‌دهد. از گزینهٔ `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const workerProcessingTime = entry.fetchStart - entry.workerStart;
    if (workerProcessingTime > 0) {
      console.log(
        `${entry.name}: Worker processing time: ${workerProcessingTime}ms`,
      );
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `resource` موجود در خط زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const workerProcessingTime = entry.fetchStart - entry.workerStart;
  if (workerProcessingTime > 0) {
    console.log(
      `${entry.name}: Worker processing time: ${workerProcessingTime}ms`,
    );
  }
});
```

### اطلاعات زمان‌بندی متقاطع (Cross-origin)

اگر مقدار ویژگی `workerStart` برابر با `0` باشد، منبع ممکن است یک درخواست متقاطع باشد. برای اجازه‌دادن به مشاهدهٔ اطلاعات زمان‌بندی متقاطع، باید هدر پاسخ {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اجازه‌دادن به `https://developer.mozilla.org` جهت مشاهدهٔ منابع زمان‌بندی، منبع متقاطع باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}