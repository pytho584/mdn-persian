---
title: "Performance: setResourceTimingBufferSize() method"
short-title: setResourceTimingBufferSize()
slug: Web/API/Performance/setResourceTimingBufferSize
page-type: web-api-instance-method
browser-compat: api.Performance.setResourceTimingBufferSize
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`setResourceTimingBufferSize()`** اندازه دلخواه بافر زمان‌بندی منابع مرورگر را تعیین می‌کند؛ بافری که ورودی‌های عملکرد `"resource"` را ذخیره می‌کند.

طبق مشخصات، بافر زمان‌بندی منابع باید در ابتدا اندازه‌ای برابر با ۲۵۰ یا بیشتر داشته باشد.

برای پاک‌کردن بافر داده‌های عملکرد منابع مرورگر، از متد {{domxref("Performance.clearResourceTimings()")}} استفاده کنید.

برای دریافت اعلان وقتی بافر زمان‌بندی منابع مرورگر پر می‌شود، به رویداد {{domxref("Performance.resourcetimingbufferfull_event", "resourcetimingbufferfull")}} گوش دهید.

## نحو (Syntax)

```js-nolint
setResourceTimingBufferSize(maxSize)
```

### پارامترها

- `maxSize`
  - : یک `number` که حداکثر تعداد اشیاء {{domxref("PerformanceEntry")}} را که مرورگر باید در بافر ورودی‌های عملکرد خود نگه دارد، مشخص می‌کند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### تنظیم اندازه بافر زمان‌بندی منابع

فراخوانی زیر اجازه می‌دهد ۵۰۰ ورودی عملکرد `"resource"` در خط زمانی عملکرد مرورگر ذخیره شود.

```js
performance.setResourceTimingBufferSize(500);
```

اگر اندازه بافر را عددی کمتر از تعداد ورودی‌های فعلی بافر تنظیم کنید، هیچ ورودی‌ای حذف نمی‌شود. در عوض، برای پاک‌کردن بافر، متد {{domxref("Performance.clearResourceTimings()")}} را فراخوانی کنید.

```js
performance.getEntriesByType("resource").length; // 20
performance.setResourceTimingBufferSize(10);
performance.getEntriesByType("resource").length; // 20

performance.clearResourceTimings();
performance.getEntriesByType("resource").length; // 0
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("Performance.clearResourceTimings()")}}
- {{domxref("Performance.resourcetimingbufferfull_event", "resourcetimingbufferfull")}}