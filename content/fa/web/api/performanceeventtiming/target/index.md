---
title: "PerformanceEventTiming: target property"
short-title: target
slug: Web/API/PerformanceEventTiming/target
page-type: web-api-instance-property
browser-compat: api.PerformanceEventTiming.target
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`target`** آخرین [`target`](/en-US/docs/Web/API/Event/target) رویداد مرتبط را برمی‌گرداند که گره‌ای (node) است که رویداد آخرین بار به آن ارسال شده است.

## مقدار

یک {{domxref("Node")}} که رویداد آخرین بار به آن ارسال شده است.

یا [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) اگر `Node` از DOM سند جدا شده باشد یا در [shadow DOM](/en-US/docs/Web/API/Web_components/Using_shadow_DOM) باشد.

## مثال‌ها

### مشاهده رویدادها با آخرین هدف مشخص

ویژگی `target` می‌تواند هنگام مشاهده ورودی‌های زمان‌بندی رویداد ({{domxref("PerformanceEventTiming")}}) استفاده شود. به عنوان مثال، برای ثبت و اندازه‌گیری رویدادها فقط برای یک آخرین هدف مشخص.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    if (entry.target && entry.target.id === "myNode") {
      const delay = entry.processingStart - entry.startTime;
      console.log(entry.name, delay);
    }
  });
});

// Register the observer for events
observer.observe({ type: "event", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}