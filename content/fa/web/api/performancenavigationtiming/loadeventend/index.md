---
title: "PerformanceNavigationTiming: loadEventEnd property"
short-title: loadEventEnd
slug: Web/API/PerformanceNavigationTiming/loadEventEnd
page-type: web-api-instance-property
browser-compat: api.PerformanceNavigationTiming.loadEventEnd
---

{{APIRef("Performance API")}}

خاصیت فقط‌خواندنی **`loadEventEnd`** یک {{domxref("DOMHighResTimeStamp")}} را برمی‌گرداند که نشان‌دهنده زمان بلافاصله پس از اتمام پردازش‌گر رویداد [`load`](/en-US/docs/Web/API/Window/load_event) سند جاری است.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده زمان بلافاصله پس از اتمام پردازش‌گر رویداد [`load`](/en-US/docs/Web/API/Window/load_event) سند جاری است.

## مثال‌ها

### اندازه‌گیری زمان پردازش‌گر رویداد `load`

از خاصیت `loadEventEnd` می‌توان برای اندازه‌گیری مدت زمان پردازش رویداد [`load`](/en-US/docs/Web/API/Window/load_event) استفاده کرد.

این کار برای اندازه‌گیری زمان اجرای پردازش‌گرهای رویداد `load` طولانی مدت مفید است.

```js
window.addEventListener("load", (event) => {
  // Some long running code
});
```

مثال با استفاده از {{domxref("PerformanceObserver")}} که با ثبت ورودی‌های جدید `navigation` در گاهشمار عملکرد مرورگر، آن‌ها را اطلاع‌رسانی می‌کند. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const loadEventTime = entry.loadEventEnd - entry.loadEventStart;
    if (loadEventTime > 0) {
      console.log(`${entry.name}: load event handler time: ${loadEventTime}ms`);
    }
  });
});

observer.observe({ type: "navigation", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}} که فقط ورودی‌های `navigation` موجود در گاهشمار عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const entries = performance.getEntriesByType("navigation");
entries.forEach((entry) => {
  const loadEventTime = entry.loadEventEnd - entry.loadEventStart;
  if (loadEventTime > 0) {
    console.log(`${entry.name}:
      load event handler time: ${loadEventTime}ms`);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد [`load`](/en-US/docs/Web/API/Window/load_event)