---
title: "PerformanceResourceTiming: serverTiming property"
---

---
title: "PerformanceResourceTiming: serverTiming property"
short-title: serverTiming
slug: Web/API/PerformanceResourceTiming/serverTiming
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.serverTiming
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`serverTiming`** آرایه‌ای از ورودی‌های {{domxref("PerformanceServerTiming")}} حاوی معیارهای زمان‌بندی سرور را برمی‌گرداند.

معیارهای زمان‌بندی سرور مستلزم آن هستند که سرور هدر {{HTTPHeader("Server-Timing")}} را ارسال کند. برای مثال:

```http
Server-Timing: cache;desc="Cache Read";dur=23.2
```

ورودی‌های `serverTiming` می‌توانند در ورودی‌های `navigation` و `resource` قرار گیرند.

## مقدار

آرایه‌ای از ورودی‌های {{domxref("PerformanceServerTiming")}}.

## مثال‌ها

### ثبت ورودی‌های زمان‌بندی سرور در لاگ

می‌توانید از {{domxref("PerformanceObserver")}} برای مشاهدهٔ ورودی‌های {{domxref("PerformanceServerTiming")}} استفاده کنید. مدت‌زمان هر ورودی سرور در کنسول ثبت می‌شود.

مثالی با استفاده از {{domxref("PerformanceObserver")}}، که هنگام ثبت ورودی‌های عملکرد جدید `resource` در خط زمانی عملکرد مرورگر اعلان می‌دهد. از گزینهٔ `buffered` برای دسترسی به ورودی‌های ثبت‌شده پیش از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    entry.serverTiming.forEach((serverEntry) => {
      console.log(`${serverEntry.name} duration: ${serverEntry.duration}`);
    });
  });
});

["navigation", "resource"].forEach((type) =>
  observer.observe({ type, buffered: true }),
);
```

مثالی با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `resource` را نشان می‌دهد که در زمان فراخوانی این متد در خط زمانی عملکرد مرورگر موجود هستند:

```js
for (const entryType of ["navigation", "resource"]) {
  for (const { name: url, serverTiming } of performance.getEntriesByType(
    entryType,
  )) {
    if (serverTiming) {
      for (const { name, duration } of serverTiming) {
        console.log(`${url}: ${name} duration: ${duration}`);
      }
    }
  }
}
```

### اطلاعات زمان‌بندی سرور در مبدأ متقاطع (Cross-origin)

دسترسی به اطلاعات زمان‌بندی سرور به همان مبدأ محدود است. برای نمایش اطلاعات زمان‌بندی در مبدأ متقاطع، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اینکه به `https://developer.mozilla.org` اجازه داده شود اطلاعات زمان‌بندی سرور را ببیند، منبع مبدأ متقاطع باید هدر زیر را ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceServerTiming")}}
- {{HTTPHeader("Server-Timing")}}