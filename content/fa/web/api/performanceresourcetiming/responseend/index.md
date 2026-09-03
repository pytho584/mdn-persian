---
title: "PerformanceResourceTiming: responseEnd property"
short-title: responseEnd
slug: Web/API/PerformanceResourceTiming/responseEnd
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.responseEnd
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`responseEnd`** یک {{domxref("DOMHighResTimeStamp","timestamp")}} را بلافاصله پس از دریافت آخرین بایت از منبع توسط مرورگر، یا بلافاصله پیش از بسته‌شدن اتصال انتقال، هر کدام زودتر رخ دهد، برمی‌گرداند.

برخلاف بسیاری از ویژگی‌های دیگر `PerformanceResourceTiming`، ویژگی `responseEnd` برای درخواست‌های cross-origin بدون نیاز به هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} در دسترس است.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} بلافاصله پس از دریافت آخرین بایت از منبع توسط مرورگر، یا بلافاصله پیش از بسته‌شدن اتصال انتقال، هر کدام زودتر رخ دهد.

## مثال‌ها

### اندازه‌گیری زمان واکشی (بدون تغییر مسیرها)

از ویژگی‌های `responseEnd` و {{domxref("PerformanceResourceTiming.fetchStart", "fetchStart")}} می‌توان برای اندازه‌گیری کل زمان واکشی منبع نهایی (بدون تغییر مسیرها) استفاده کرد. اگر بخواهید تغییر مسیرها را نیز لحاظ کنید، کل زمان واکشی در ویژگی {{domxref("PerformanceEntry.duration", "duration")}} ارائه می‌شود.

```js
const timeToFetch = entry.responseEnd - entry.fetchStart;
```

مثال زیر از {{domxref("PerformanceObserver")}} استفاده می‌کند، که با ثبت ورودی‌های عملکردی جدید از نوع `resource` در خط زمانی عملکرد مرورگر، اطلاع می‌دهد. برای دسترسی به ورودی‌های مربوط به قبل از ایجاد observer، از گزینه `buffered` استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const timeToFetch = entry.responseEnd - entry.fetchStart;
    if (timeToFetch > 0) {
      console.log(`${entry.name}: Time to fetch: ${timeToFetch}ms`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند، که فقط ورودی‌های عملکردی از نوع `resource` موجود در خط زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const timeToFetch = entry.responseEnd - entry.fetchStart;
  if (timeToFetch > 0) {
    console.log(`${entry.name}: Time to fetch: ${timeToFetch}ms`);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}
