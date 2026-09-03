---
title: "Performance: clearResourceTimings() method"
short-title: clearResourceTimings()
slug: Web/API/Performance/clearResourceTimings
page-type: web-api-instance-method
browser-compat: api.Performance.clearResourceTimings
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`clearResourceTimings()`** تمام ورودی‌های عملکرد (PerformanceEntry) با {{domxref("PerformanceEntry.entryType","entryType")}} برابر با `"resource"` را از جدول زمانی عملکرد مرورگر حذف می‌کند و اندازه بافر داده منابع عملکرد را به صفر بازنشانی می‌کند.

برای تنظیم اندازه بافر داده منابع عملکرد مرورگر، از متد {{domxref("Performance.setResourceTimingBufferSize()")}} استفاده کنید.

برای دریافت اعلان هنگام پر شدن بافر زمان‌بندی منابع مرورگر، به رویداد {{domxref("Performance.resourcetimingbufferfull_event", "resourcetimingbufferfull")}} گوش دهید.

## نحو (Syntax)

```js-nolint
clearResourceTimings()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### پاک کردن بافر داده منابع عملکرد

برای حذف تمام ورودی‌های عملکرد منابع از بافر، متد `clearResourceTimings()` را در نقطه مناسب کد خود فراخوانی کنید یا آن را در کنسول قرار دهید.

```js
performance.clearResourceTimings();
performance.getEntriesByType("resource").length; // 0
```

### ثبت رکوردها و خالی کردن PerformanceObserver

هنگام استفاده از اشیاء {{domxref("PerformanceObserver")}} (به‌ویژه وقتی پرچم `buffered` روی `true` تنظیم شده باشد)، بافر منابع عملکرد ممکن است به سرعت پر شود. با این حال، به جای پاک کردن بافر، می‌توانید فهرست فعلی ورودی‌های عملکرد را ذخیره کرده و با استفاده از متد {{domxref("PerformanceObserver.takeRecords()")}} مشاهده‌گر عملکرد را خالی کنید. این روش با انواع مختلف ورودی‌های عملکرد کار می‌کند، نه فقط ورودی‌های `"resource"`.

```js
function perfObserver(list, observer) {
  list.getEntries().forEach((entry) => {
    // do something with the entries
  });
}
const observer = new PerformanceObserver(perfObserver);
observer.observe({ type: "resource", buffered: true });

// Store entries and empty performance observer
const records = observer.takeRecords();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Performance.setResourceTimingBufferSize()")}}
- {{domxref("Performance.resourcetimingbufferfull_event", "resourcetimingbufferfull")}}