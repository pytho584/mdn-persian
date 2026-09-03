---
title: "PerformanceEventTiming: processingEnd property"
short-title: processingEnd
slug: Web/API/PerformanceEventTiming/processingEnd
page-type: web-api-instance-property
browser-compat: api.PerformanceEventTiming.processingEnd
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`processingEnd`** زمان پایان اجرای آخرین مدیریت‌کننده رویداد (event handler) را برمی‌گرداند.

در نبود چنین مدیریت‌کننده‌های رویدادی، مقدار آن با {{domxref("PerformanceEventTiming.processingStart")}} برابر است.

## مقدار

یک برچسب زمانی از نوع {{domxref("DOMHighResTimeStamp")}}.

## مثال‌ها

### استفاده از ویژگی processingEnd

از ویژگی `processingEnd` می‌توان هنگام مشاهده ورودی‌های زمان‌بندی رویداد ({{domxref("PerformanceEventTiming")}}) استفاده کرد؛ مثلاً برای محاسبه تأخیر ورودی یا زمان‌های پردازش رویداد.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    // Full duration
    const duration = entry.duration;
    // Input delay (before processing event)
    const delay = entry.processingStart - entry.startTime;
    // Synchronous event processing time
    // (between start and end dispatch)
    const time = entry.processingEnd - entry.processingStart;
  });
});
// Register the observer for events
observer.observe({ type: "event", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("PerformanceEventTiming.processingStart")}}