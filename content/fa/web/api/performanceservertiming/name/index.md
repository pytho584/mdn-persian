---
title: "PerformanceServerTiming: name property"
short-title: name
slug: Web/API/PerformanceServerTiming/name
page-type: web-api-instance-property
browser-compat: api.PerformanceServerTiming.name
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

خاصیت فقط خواندنی **`name`** یک رشته (string) شامل نام معیار (metric) مشخص‌شده توسط سرور را برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

### ثبت ورودی‌های زمان‌بندی سرور

معیارهای زمان‌بندی سرور نیاز دارند که سرور هدر {{HTTPHeader("Server-Timing")}} را ارسال کند. به عنوان مثال:

```http
Server-Timing: cache;desc="Cache Read";dur=23.2
```

ورودی‌های `serverTiming` می‌توانند در ورودی‌های `navigation` و `resource` قرار داشته باشند.

مثال با استفاده از {{domxref("PerformanceObserver")}} که هنگام ثبت ورودی‌های جدید عملکرد (performance) از نوع `navigation` و `resource` در جدول زمانی عملکرد مرورگر، اعلان می‌دهد. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

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

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}} که فقط ورودی‌های عملکرد `navigation` و `resource` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

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

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceServerTiming")}}
- {{HTTPHeader("Server-Timing")}}