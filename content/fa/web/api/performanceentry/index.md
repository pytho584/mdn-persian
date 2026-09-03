---
title: PerformanceEntry
slug: Web/API/PerformanceEntry
page-type: web-api-interface
browser-compat: api.PerformanceEntry
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

شیء **`PerformanceEntry`** یک معیار عملکرد واحد را که بخشی از زمان‌بند عملکرد (performance timeline) مرورگر است، کپسوله می‌کند.

Performance API معیارهای داخلی ارائه می‌دهد که زیرکلاس‌های تخصصی `PerformanceEntry` هستند. این شامل ورودی‌هایی برای بارگذاری منابع، زمان‌بندی رویدادها و موارد دیگر است.

یک ورودی عملکرد همچنین می‌تواند با فراخوانی متدهای {{domxref("Performance.mark()")}} یا {{domxref("Performance.measure()")}} در یک نقطه مشخص از برنامه ایجاد شود. این به شما امکان می‌دهد معیارهای خود را به زمان‌بند عملکرد اضافه کنید.

نمونه‌های `PerformanceEntry` همیشه یکی از زیرکلاس‌های زیر خواهند بود:

- {{domxref("LargestContentfulPaint")}}
- {{domxref("LayoutShift")}}
- {{domxref("PerformanceEventTiming")}}
- {{domxref("PerformanceLongAnimationFrameTiming")}}
- {{domxref("PerformanceLongTaskTiming")}}
- {{domxref("PerformanceMark")}}
- {{domxref("PerformanceMeasure")}}
- {{domxref("PerformanceNavigationTiming")}}
- {{domxref("PerformancePaintTiming")}}
- {{domxref("PerformanceResourceTiming")}}
- {{domxref("PerformanceScriptTiming")}}
- {{domxref("PerformanceServerTiming")}}
- {{domxref("TaskAttributionTiming")}}
- {{domxref("VisibilityStateEntry")}}

## ویژگی‌های نمونه

- {{domxref("PerformanceEntry.name")}} {{ReadOnlyInline}}
  - : یک رشته که نام یک ورودی عملکرد را نشان می‌دهد. مقدار آن به زیرنوع بستگی دارد.
- {{domxref("PerformanceEntry.entryType")}} {{ReadOnlyInline}}
  - : یک رشته که نوع معیار عملکرد را نشان می‌دهد. به عنوان مثال، `"mark"` زمانی که از {{domxref("PerformanceMark")}} استفاده شود.
- {{domxref("PerformanceEntry.startTime")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که زمان شروع معیار عملکرد را نشان می‌دهد.
- {{domxref("PerformanceEntry.duration")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که مدت زمان ورودی عملکرد را نشان می‌دهد.

## روش‌های نمونه

- {{domxref("PerformanceEntry.toJSON","PerformanceEntry.toJSON()")}}
  - : یک نمایش JSON از شیء `PerformanceEntry` برمی‌گرداند.

## مثال

### کار با ورودی‌های عملکرد

مثال زیر اشیاء `PerformanceEntry` از نوع {{domxref("PerformanceMark")}} و {{domxref("PerformanceMeasure")}} ایجاد می‌کند. زیرکلاس‌های `PerformanceMark` و `PerformanceMeasure` ویژگی‌های `duration`، `entryType`، `name` و `startTime` را از `PerformanceEntry` به ارث برده و آن‌ها را به مقادیر مناسب خود تنظیم می‌کنند.

```js
// در مکانی از کد که ورود (login) شروع می‌شود قرار دهید
performance.mark("login-started");

// در مکانی از کد که ورود پایان می‌یابد قرار دهید
performance.mark("login-finished");

// مدت زمان ورود را اندازه‌گیری کنید
performance.measure("login-duration", "login-started", "login-finished");

function perfObserver(list, observer) {
  list.getEntries().forEach((entry) => {
    if (entry.entryType === "mark") {
      console.log(`${entry.name}'s startTime: ${entry.startTime}`);
    }
    if (entry.entryType === "measure") {
      console.log(`${entry.name}'s duration: ${entry.duration}`);
    }
  });
}
const observer = new PerformanceObserver(perfObserver);
observer.observe({ entryTypes: ["measure", "mark"] });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}