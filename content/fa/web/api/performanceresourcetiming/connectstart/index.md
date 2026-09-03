---
title: "PerformanceResourceTiming: connectStart property"
short-title: connectStart
slug: Web/API/PerformanceResourceTiming/connectStart
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.connectStart
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`connectStart`**، {{domxref("DOMHighResTimeStamp","timestamp")}} را بلافاصله قبل از شروع عامل کاربر (user agent) برای برقراری اتصال به سرور جهت بازیابی منبع (resource) برمی‌گرداند.

## مقدار

ویژگی `connectStart` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp")}} بلافاصله قبل از اینکه مرورگر شروع به برقراری اتصال به سرور برای بازیابی منبع کند.
- اگر منبع به‌طور آنی از حافظهٔ پنهان (cache) بازیابی شود، مقدار `0`.
- اگر منبع یک درخواست متقاطع (cross-origin) باشد و هیچ هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشود، مقدار `0`.

## مثال‌ها

### اندازه‌گیری زمان دست‌دهی TCP

از ویژگی‌های `connectStart` و {{domxref("PerformanceResourceTiming.connectEnd", "connectEnd")}} می‌توان برای اندازه‌گیری مدت‌زمان لازم برای انجام دست‌دهی TCP استفاده کرد.

```js
const tcp = entry.connectEnd - entry.connectStart;
```

مثال با استفاده از {{domxref("PerformanceObserver")}}، که هنگام ثبت ورودی‌های جدید performance از نوع `resource` در جدول زمانی عملکرد مرورگر، اطلاع می‌دهد. برای دسترسی به ورودی‌های قبل از ایجاد مشاهده‌گر، از گزینهٔ `buffered` استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const tcp = entry.connectEnd - entry.connectStart;
    if (tcp > 0) {
      console.log(`${entry.name}: TCP handshake duration: ${tcp}ms`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های performance از نوع `resource` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const tcp = entry.connectEnd - entry.connectStart;
  if (tcp > 0) {
    console.log(`${entry.name}: TCP handshake duration: ${tcp}ms`);
  }
});
```

### اطلاعات زمان‌بندی متقاطع (Cross-origin)

اگر مقدار ویژگی `connectStart` برابر `0` باشد، منبع ممکن است یک درخواست متقاطع باشد. برای فراهم کردن امکان دیدن اطلاعات زمان‌بندی متقاطع، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اینکه `https://developer.mozilla.org` اجازهٔ دیدن منابع زمان‌بندی را داشته باشد، منبع متقاطع باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}