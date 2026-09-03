---
title: "PerformanceResourceTiming: fetchStart property"
short-title: fetchStart
slug: Web/API/PerformanceResourceTiming/fetchStart
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.fetchStart
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`fetchStart`** یک {{domxref("DOMHighResTimeStamp","زمان‌سنج")}} را بلافاصله قبل از شروع مرورگر به واکشی (fetch) منبع، نشان می‌دهد.

اگر تغییرمسیرهای HTTP وجود داشته باشد، این ویژگی زمان را بلافاصله قبل از اینکه عامل کاربر شروع به واکشی منبع نهایی در تغییرمسیر کند، برمی‌گرداند.

برخلاف بسیاری از ویژگی‌های دیگر `PerformanceResourceTiming`، ویژگی `fetchStart` برای درخواست‌های بین‌نشانی (cross-origin) بدون نیاز به هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} در دسترس است.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} بلافاصله قبل از شروع مرورگر به واکشی منبع.

## مثال‌ها

### اندازه‌گیری زمان واکشی (بدون تغییرمسیر)

از ویژگی‌های `fetchStart` و {{domxref("PerformanceResourceTiming.responseEnd", "responseEnd")}} می‌توان برای اندازه‌گیری زمان کل مورد نیاز برای واکشی منبع نهایی (بدون تغییرمسیر) استفاده کرد. اگر می‌خواهید تغییرمسیرها را نیز شامل کنید، زمان کل واکشی در ویژگی {{domxref("PerformanceEntry.duration", "duration")}} ارائه می‌شود.

```js
const timeToFetch = entry.responseEnd - entry.fetchStart;
```

مثال با استفاده از {{domxref("PerformanceObserver")}} که هنگام ثبت ورودی‌های عملکرد `resource` جدید در جدول زمانی عملکرد مرورگر، اطلاع‌رسانی می‌کند. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد ناظر استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const timeToFetch = entry.responseEnd - entry.fetchStart;
    if (timeToFetch > 0) {
      console.log(`${entry.name}: زمان واکشی: ${timeToFetch}ms`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}} که فقط ورودی‌های عملکرد `resource` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const timeToFetch = entry.responseEnd - entry.fetchStart;
  if (timeToFetch > 0) {
    console.log(`${entry.name}: زمان واکشی: ${timeToFetch}ms`);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}