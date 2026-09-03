---
title: "PerformanceResourceTiming: domainLookupEnd property"
short-title: domainLookupEnd
slug: Web/API/PerformanceResourceTiming/domainLookupEnd
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.domainLookupEnd
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`domainLookupEnd`**، {{domxref("DOMHighResTimeStamp","timestamp")}} را بلافاصله پس از پایان جستجوی نام دامنه (DNS lookup) توسط مرورگر برای منبع بازمی‌گرداند.

اگر عامل کاربر اطلاعات دامنه را در حافظه نهان (cache) داشته باشد، {{domxref("PerformanceResourceTiming.domainLookupStart","domainLookupStart")}} و `domainLookupEnd` نشان‌دهنده زمان شروع و پایان بازیابی داده‌های دامنه از حافظه نهان هستند.

## مقدار

خاصیت `domainLookupEnd` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp")}} که زمان بلافاصله پس از پایان جستجوی نام دامنه توسط مرورگر برای منبع را نشان می‌دهد.
- `0` اگر منبع به‌طور لحظه‌ای از حافظه نهان بازیابی شده باشد.
- `0` اگر منبع یک درخواست متقاطع-ریشه (cross-origin) باشد و هیچ هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد.

## مثال‌ها

### اندازه‌گیری زمان جستجوی DNS

از خاصیت‌های `domainLookupEnd` و {{domxref("PerformanceResourceTiming.domainLookupStart", "domainLookupStart")}} می‌توان برای اندازه‌گیری مدت زمان جستجوی DNS استفاده کرد.

```js
const dns = entry.domainLookupEnd - entry.domainLookupStart;
```

مثال با استفاده از {{domxref("PerformanceObserver")}}، که با ثبت ورودی‌های جدید `resource` در جدول زمانی عملکرد مرورگر، آن‌ها را اعلام می‌کند. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const dns = entry.domainLookupEnd - entry.domainLookupStart;
    if (dns > 0) {
      console.log(`${entry.name}: مدت زمان جستجوی DNS: ${dns}ms`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `resource` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const dns = entry.domainLookupEnd - entry.domainLookupStart;
  if (dns > 0) {
    console.log(`${entry.name}: مدت زمان جستجوی DNS: ${dns}ms`);
  }
});
```

### اطلاعات زمان‌بندی درخواست‌های متقاطع-ریشه

اگر مقدار خاصیت `domainLookupEnd` برابر `0` باشد، ممکن است منبع یک درخواست متقاطع-ریشه باشد. برای مشاهده اطلاعات زمان‌بندی متقاطع-ریشه، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

به عنوان مثال، برای اجازه دادن به `https://developer.mozilla.org` برای دیدن منابع زمان‌بندی، منبع متقاطع-ریشه باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}