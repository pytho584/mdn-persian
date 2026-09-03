---
title: "PerformanceServerTiming: toJSON() method"
short-title: toJSON()
slug: Web/API/PerformanceServerTiming/toJSON
page-type: web-api-instance-method
browser-compat: api.PerformanceServerTiming.toJSON
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`toJSON()`** از رابط {{domxref("PerformanceServerTiming")}} یک {{Glossary("Serialization","سریال‌ساز")}} است؛ یک نمایش JSON از شیء {{domxref("PerformanceServerTiming")}} را برمی‌گرداند.

## Syntax

```js-nolint
toJSON()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازی شده‌ی شیء {{domxref("PerformanceServerTiming")}} است.

## مثال‌ها

### ثبت ورودی‌های زمان‌بندی سرور

معیارهای زمان‌بندی سرور نیاز دارند که سرور هدر {{HTTPHeader("Server-Timing")}} را ارسال کند. برای مثال:

```http
Server-Timing: cache;desc="Cache Read";dur=23.2
```

ورودی‌های `serverTiming` می‌توانند روی ورودی‌های `navigation` و `resource` قرار داشته باشند.

مثال با استفاده از {{domxref("PerformanceObserver")}}، که وقتی ورودی‌های عملکرد جدید `navigation` و `resource` در جدول زمانی عملکرد مرورگر ثبت می‌شوند، اطلاع‌رسانی می‌کند. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    entry.serverTiming.forEach((serverEntry) => {
      console.log(serverEntry.toJSON());
    });
  });
});

["navigation", "resource"].forEach((type) =>
  observer.observe({ type, buffered: true }),
);
```

این کار یک شیء JSON مانند زیر را ثبت می‌کند:

```json
{
  "name": "cache",
  "duration": 23.2,
  "description": "Cache Read"
}
```

برای دریافت یک رشته JSON، می‌توانید مستقیماً از [`JSON.stringify(serverEntry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد به طور خودکار `toJSON()` را فراخوانی می‌کند.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}