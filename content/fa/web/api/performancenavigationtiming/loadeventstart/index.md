---
title: "PerformanceNavigationTiming: loadEventStart property"
short-title: loadEventStart
slug: Web/API/PerformanceNavigationTiming/loadEventStart
page-type: web-api-instance-property
browser-compat: api.PerformanceNavigationTiming.loadEventStart
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`loadEventStart`** یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که زمانِ دقیقاً قبل از شروع اجرای کنترل‌کننده رویداد [`load`](/en-US/docs/Web/API/Window/load_event) سندِ فعلی را نشان می‌دهد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} که زمانِ دقیقاً قبل از شروع کنترل‌کننده رویداد [`load`](/en-US/docs/Web/API/Window/load_event) سندِ فعلی را نشان می‌دهد.

## مثال‌ها

### اندازه‌گیری زمان اجرای کنترل‌کننده رویداد `load`

از ویژگی `loadEventStart` می‌توان برای اندازه‌گیری مدت زمانی که صرف پردازش کنترل‌کننده رویداد [`load`](/en-US/docs/Web/API/Window/load_event) می‌شود استفاده کرد.

این کار برای اندازه‌گیری زمان اجرای کنترل‌کننده‌های رویداد [`load`](/en-US/docs/Web/API/Window/load_event) که مدت‌زمان طولانی‌ای می‌گیرند مفید است.

```js
window.addEventListener("load", (event) => {
  // Some long running code
});
```

مثال زیر از {{domxref("PerformanceObserver")}} استفاده می‌کند که به‌محض ثبت ورودی‌های عملکردی `navigation` در خط زمانی عملکرد مرورگر، ورودی‌های جدید را اطلاع می‌دهد. برای دسترسی به ورودی‌های پیش از ساخته‌شدن observer، از گزینه `buffered` استفاده کنید.

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

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند که فقط ورودی‌های عملکردی `navigation` موجود در خط زمانی عملکرد مرورگر را در لحظه فراخوانی این متد نشان می‌دهد:

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