---
title: "PerformanceServerTiming: description property"
short-title: description
slug: Web/API/PerformanceServerTiming/description
page-type: web-api-instance-property
browser-compat: api.PerformanceServerTiming.description
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

خاصیت فقط-خواندنی **`description`** یک رشته از توضیح معیار (metric) مشخص‌شده توسط سرور را برمی‌گرداند، یا در صورت عدم وجود، یک رشته خالی.

## مقدار

یک مقدار از نوع رشته.

## مثال‌ها

### ثبت ورودی‌های زمان‌بندی سرور

معیارهای زمان‌بندی سرور (server timing metrics) نیاز دارند که سرور هدر {{HTTPHeader("Server-Timing")}} را ارسال کند. برای مثال:

```http
Server-Timing: cache;desc="Cache Read";dur=23.2
```

ورودی‌های `serverTiming` می‌توانند در ورودی‌های `navigation` و `resource` قرار داشته باشند.

مثالی با استفاده از {{domxref("PerformanceObserver")}}، که هنگام ثبت ورودی‌های جدید عملکرد `navigation` و `resource` در timeline عملکرد مرورگر، اطلاع‌رسانی می‌کند. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    entry.serverTiming.forEach((serverEntry) => {
      console.log(
        `${sererEntry.name} (${sererEntry.description}) duration: ${sererEntry.duration}`,
      );
      // لاگ می‌کند "cache (Cache Read) duration: 23.2"
    });
  });
});

["navigation", "resource"].forEach((type) =>
  observer.observe({ type, buffered: true }),
);
```

مثالی با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `navigation` و `resource` موجود در timeline عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
for (const entryType of ["navigation", "resource"]) {
  for (const { name: url, serverTiming } of performance.getEntriesByType(
    entryType,
  )) {
    if (serverTiming) {
      for (const { name, description, duration } of serverTiming) {
        console.log(`${name} (${description}) duration: ${duration}`);
        // لاگ می‌کند "cache (Cache Read) duration: 23.2"
      }
    }
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceServerTiming")}}
- {{HTTPHeader("Server-Timing")}}