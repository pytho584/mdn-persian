---
title: "PerformanceEventTiming: cancelable property"
---

---
title: "PerformanceEventTiming: cancelable property"
short-title: cancelable
slug: Web/API/PerformanceEventTiming/cancelable
page-type: web-api-instance-property
browser-compat: api.PerformanceEventTiming.cancelable
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`cancelable`**، ویژگی [`cancelable`](/en-US/docs/Web/API/Event/cancelable) رویداد مرتبط را برمی‌گرداند و نشان می‌دهد که آیا رویداد قابل لغو است یا خیر.

## مقدار

یک مقدار بولی. اگر رویداد مرتبط قابل لغو باشد، `true` و در غیر این صورت `false` است.

## مثال‌ها

### مشاهده رویدادهای غیرقابل لغو

ویژگی `cancelable` می‌تواند هنگام مشاهده ورودی‌های زمان‌بندی رویداد ({{domxref("PerformanceEventTiming")}}) استفاده شود. برای مثال، می‌توان صرفاً رویدادهای غیرقابل لغو را ثبت و اندازه‌گیری کرد.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    if (!entry.cancelable) {
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

## سازگاری با مرورگرها

{{Compat}}