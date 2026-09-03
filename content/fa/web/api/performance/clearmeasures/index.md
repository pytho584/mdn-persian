---
title: "Performance: clearMeasures() method"
short-title: clearMeasures()
slug: Web/API/Performance/clearMeasures
page-type: web-api-instance-method
browser-compat: api.Performance.clearMeasures
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`clearMeasures()`** تمام یا اشیاء خاص {{domxref("PerformanceMeasure")}} را از خط زمانی عملکرد (performance timeline) مرورگر حذف می‌کند.

## نحو

```js-nolint
clearMeasures()
clearMeasures(name)
```

### پارامترها

- `name` {{optional_inline}}
  - : یک رشته که {{domxref("PerformanceEntry.name", "name")}} (نام) شیء {{domxref("PerformanceMeasure")}} را نشان می‌دهد. اگر این آرگومان حذف شود، تمام ورودی‌هایی که {{domxref("PerformanceEntry.entryType","entryType")}} آنها `"measure"` است حذف خواهند شد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

### حذف اندازه‌گیری‌ها

برای پاک کردن تمام اندازه‌گیری‌های عملکرد (performance measures) یا فقط ورودی‌های خاص، از متد `clearMeasures()` به این صورت استفاده کنید:

```js
// ایجاد چندین اندازه‌گیری
performance.measure("from navigation");
performance.mark("a");
performance.measure("from mark a", "a");
performance.measure("from navigation");
performance.measure("from mark a", "a");
performance.mark("b");
performance.measure("between a and b", "a", "b");

performance.getEntriesByType("measure").length; // 5

// فقط ورودی‌های اندازه‌گیری "from navigation" را حذف کن
performance.clearMeasures("from navigation");
performance.getEntriesByType("measure").length; // 3

// تمام ورودی‌های اندازه‌گیری را حذف کن
performance.clearMeasures();
performance.getEntriesByType("measure").length; // 0
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceMeasure")}}