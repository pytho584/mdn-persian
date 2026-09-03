---
title: "PerformanceEventTiming: processingStart property"
short-title: processingStart
slug: Web/API/PerformanceEventTiming/processingStart
page-type: web-api-instance-property
browser-compat: api.PerformanceEventTiming.processingStart
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`processingStart`**، زمانی را برمی‌گرداند که ارسال رویداد (event dispatch) آغاز شده است؛ یعنی زمانی که کنترل‌کننده‌های رویداد در آستانهٔ اجرا قرار دارند.

## مقدار

یک مهر زمانی از نوع {{domxref("DOMHighResTimeStamp")}}.

## مثال‌ها

### استفاده از ویژگی processingStart

ویژگی `processingStart` را می‌توان هنگام مشاهدهٔ ورودی‌های زمان‌بندی رویداد ({{domxref("PerformanceEventTiming")}}) به کار برد؛ برای مثال، برای محاسبهٔ تأخیر ورودی یا زمان‌های پردازش رویداد.

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

## همچنین ببینید

- {{domxref("PerformanceEventTiming.processingEnd")}}