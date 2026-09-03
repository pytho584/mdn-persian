---
title: "PerformanceServerTiming: duration property"
short-title: duration
slug: Web/API/PerformanceServerTiming/duration
page-type: web-api-instance-property
browser-compat: api.PerformanceServerTiming.duration
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`duration`** یک عدد اعشاری (double) برمی‌گرداند که مدت زمان مشخص‌شده توسط سرور (معمولاً بر حسب میلی‌ثانیه) یا مقدار `0.0` را دربردارد.

## مقدار

یک عدد.

## مثال‌ها

### ثبت ورودی‌های زمان‌بندی سرور

برای متریک‌های زمان‌بندی سرور، لازم است سرور هدر {{HTTPHeader("Server-Timing")}} را ارسال کند. برای مثال:

```http
Server-Timing: cache;desc="Cache Read";dur=23.2
```

ورودی‌های `serverTiming` می‌توانند روی ورودی‌های `navigation` و `resource` قرار بگیرند.

مثال زیر با استفاده از {{domxref("PerformanceObserver")}}، ورودی‌های عملکرد جدید `navigation` و `resource` را هنگام ثبت شدن در خط زمانی عملکرد مرورگر اطلاع‌رسانی می‌کند. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    entry.serverTiming.forEach((serverEntry) => {
      console.log(
        `${serverEntry.name} (${serverEntry.description}) duration: ${serverEntry.duration}`,
      );
      // Logs "cache (Cache Read) duration: 23.2"
    });
  });
});

["navigation", "resource"].forEach((type) =>
  observer.observe({ type, buffered: true }),
);
```

مثال زیر با استفاده از {{domxref("Performance.getEntriesByType()")}}، فقط ورودی‌های عملکرد `navigation` و `resource` را نشان می‌دهد که در زمان فراخوانی این متد در خط زمانی عملکرد مرورگر وجود دارند:

```js
for (const entryType of ["navigation", "resource"]) {
  for (const { name: url, serverTiming } of performance.getEntriesByType(
    entryType,
  )) {
    if (serverTiming) {
      for (const { name, description, duration } of serverTiming) {
        console.log(`${name} (${description}) duration: ${duration}`);
        // Logs "cache (Cache Read) duration: 23.2"
      }
    }
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceServerTiming")}}
- {{HTTPHeader("Server-Timing")}}