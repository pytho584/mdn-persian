---
title: PerformanceServerTiming
slug: Web/API/PerformanceServerTiming
page-type: web-api-interface
browser-compat: api.PerformanceServerTiming
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}{{securecontext_header}}

رابط **`PerformanceServerTiming`** معیارهای سرور را که همراه با پاسخ در هدر HTTP {{HTTPHeader("Server-Timing")}} ارسال می‌شوند، نمایش می‌دهد.

این رابط به همان مبدأ (origin) محدود می‌شود، اما می‌توانید از هدر {{HTTPHeader("Timing-Allow-Origin")}} برای تعیین دامنه‌هایی که مجاز به دسترسی به معیارهای سرور هستند استفاده کنید. توجه داشته باشید که این رابط فقط در زمینه‌های امن (HTTPS) در برخی مرورگرها در دسترس است.

## ویژگی‌های نمونه

- {{domxref('PerformanceServerTiming.description')}} {{ReadOnlyInline}}
  - : یک مقدار رشته‌ای از توضیحات معیار مشخص‌شده توسط سرور، یا یک رشته خالی.
- {{domxref('PerformanceServerTiming.duration')}} {{ReadOnlyInline}}
  - : یک عدد اعشاری (double) که مدت‌زمان معیار مشخص‌شده توسط سرور را شامل می‌شود، یا مقدار `0.0`.
- {{domxref('PerformanceServerTiming.name')}} {{ReadOnlyInline}}
  - : یک مقدار رشته‌ای از نام معیار مشخص‌شده توسط سرور.

## روش‌های نمونه

- {{domxref('PerformanceServerTiming.toJSON()')}}
  - : یک نمایش JSON از شیء `PerformanceServerTiming` برمی‌گرداند.

## مثال

با فرض اینکه سروری هدر {{HTTPHeader("Server-Timing")}} را ارسال کند، مثلاً یک سرور Node.js مانند این:

```js
const http = require("http");

function requestHandler(request, response) {
  const headers = {
    "Server-Timing": `
      cache;desc="Cache Read";dur=23.2,
      db;dur=53,
      app;dur=47.2
    `.replace(/\n/g, ""),
  };
  response.writeHead(200, headers);
  response.write("");
  return setTimeout(() => {
    response.end();
  }, 1000);
}

http.createServer(requestHandler).listen(3000).on("error", console.error);
```

اکنون ورودی‌های `PerformanceServerTiming` از طریق ویژگی {{domxref("PerformanceResourceTiming.serverTiming")}} در جاوااسکریپت قابل مشاهده‌اند و روی ورودی‌های `navigation` و `resource` قرار می‌گیرند.

مثالی با استفاده از {{domxref("PerformanceObserver")}} که وقتی ورودی‌های عملکرد جدید `navigation` و `resource` در خط زمانی عملکرد مرورگر ثبت می‌شوند، اطلاع می‌دهد. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    entry.serverTiming.forEach((serverEntry) => {
      console.log(
        `${serverEntry.name} (${serverEntry.description}) duration: ${serverEntry.duration}`,
      );
      // Logs "cache (Cache Read) duration: 23.2"
      // Logs "db () duration: 53"
      // Logs "app () duration: 47.2"
    });
  });
});

["navigation", "resource"].forEach((type) =>
  observer.observe({ type, buffered: true }),
);
```

مثالی با استفاده از {{domxref("Performance.getEntriesByType()")}} که فقط ورودی‌های عملکرد `navigation` و `resource` موجود در خط زمانی عملکرد مرورگر را در زمانی که این متد را فراخوانی می‌کنید نشان می‌دهد:

```js
for (const entryType of ["navigation", "resource"]) {
  for (const { name: url, serverTiming } of performance.getEntriesByType(
    entryType,
  )) {
    if (serverTiming) {
      for (const { name, description, duration } of serverTiming) {
        console.log(`${name} (${description}) duration: ${duration}`);
        // Logs "cache (Cache Read) duration: 23.2"
        // Logs "db () duration: 53"
        // Logs "app () duration: 47.2"
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

- {{HTTPHeader("Server-Timing")}}
- {{domxref("PerformanceResourceTiming.serverTiming")}}