---
title: "PerformanceObserver: disconnect() method"
short-title: disconnect()
slug: Web/API/PerformanceObserver/disconnect
page-type: web-api-instance-method
browser-compat: api.PerformanceObserver.disconnect
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`disconnect()`** از رابط {{domxref('PerformanceObserver')}} باعث می‌شود که مشاهده‌گر عملکرد دیگر هیچ رویداد {{domxref("PerformanceEntry","performance entry", '', 'true')}} دریافت نکند.

## سینتکس

```js-nolint
disconnect()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### توقف یک مشاهده‌گر عملکرد

در مثال زیر، مشاهده‌گر عملکرد قطع می‌شود تا دیگر هیچ رویداد performance entry دریافت نکند.

```js
const observer = new PerformanceObserver((list, obj) => {
  list.getEntries().forEach((entry) => {
    // Process "measure" events
    // …
    // Disable additional performance events
    observer.disconnect();
  });
});
observer.observe({ entryTypes: ["mark", "measure"] });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}