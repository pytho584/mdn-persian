---
title: "PerformanceObserver: takeRecords() method"
short-title: takeRecords()
slug: Web/API/PerformanceObserver/takeRecords
page-type: web-api-instance-method
browser-compat: api.PerformanceObserver.takeRecords
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`takeRecords()`** در رابط {{domxref('PerformanceObserver')}} فهرست کنونی از اشیاء {{domxref("PerformanceEntry")}} ذخیره‌شده در observer را برمی‌گرداند و آن را خالی می‌کند.

## نحو (Syntax)

```js-nolint
takeRecords()
```

### پارامترها

هیچ.

### مقدار بازگشتی

فهرستی از اشیاء {{domxref("PerformanceEntry")}}.

## مثال‌ها

### گرفتن records

مثال زیر فهرست کنونی از ورودی‌های عملکرد را در `records` ذخیره می‌کند و observer را خالی می‌کند.

```js
const observer = new PerformanceObserver((list, obj) => {
  list.getEntries().forEach((entry) => {
    // Process "mark" and "measure" events
  });
});
observer.observe({ entryTypes: ["mark", "measure"] });
const records = observer.takeRecords();
console.log(records[0].name);
console.log(records[0].startTime);
console.log(records[0].duration);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}