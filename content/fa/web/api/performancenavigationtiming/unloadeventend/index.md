---
title: "PerformanceNavigationTiming: unloadEventEnd property"
short-title: unloadEventEnd
slug: Web/API/PerformanceNavigationTiming/unloadEventEnd
page-type: web-api-instance-property
browser-compat: api.PerformanceNavigationTiming.unloadEventEnd
---

{{APIRef("Performance API")}}

خاصیت **`unloadEventEnd`** (فقط خواندنی) یک {{domxref("DOMHighResTimeStamp")}} را برمی‌گرداند که نشان‌دهندهٔ زمان دقیقاً پس از اتمام اجرای مدیریت‌کنندهٔ رویداد [`unload`](/en-US/docs/Web/API/Window/unload_event) سند قبلی است.

## مقدار

خاصیت `unloadEventEnd` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهندهٔ زمان دقیقاً پس از اتمام اجرای مدیریت‌کنندهٔ رویداد [`unload`](/en-US/docs/Web/API/Window/unload_event) سند قبلی است.
- `0` در صورتی که سند قبلی وجود نداشته باشد.
- `0` در صورتی که صفحهٔ قبلی در یک خاستگاه دیگر بوده باشد.

## مثال‌ها

### اندازه‌گیری زمان مدیریت‌کنندهٔ رویداد `unload`

از خاصیت `unloadEventEnd` می‌توان برای اندازه‌گیری مدت زمان پردازش مدیریت‌کنندهٔ رویداد [`unload`](/en-US/docs/Web/API/Window/unload_event) استفاده کرد.

این کار برای اندازه‌گیری زمان اجرای مدیریت‌کننده‌های رویداد [`unload`](/en-US/docs/Web/API/Window/load_event) طولانی‌مدت مفید است.

```js
window.addEventListener("unload", (event) => {
  // Some long running code
});
```

مثال با استفاده از {{domxref("PerformanceObserver")}} که به محض ثبت ورودی‌های جدید عملکرد `navigation` در جدول زمانی عملکرد مرورگر، آن‌ها را اعلام می‌کند. از گزینهٔ `buffered` برای دسترسی به ورودی‌های قبل از ایجاد ناظر استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const unloadEventTime = entry.unloadEventEnd - entry.unloadEventStart;
    if (unloadEventTime > 0) {
      console.log(
        `${entry.name}: unload event handler time: ${unloadEventTime}ms`,
      );
    }
  });
});

observer.observe({ type: "navigation", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}} که فقط ورودی‌های عملکرد `navigation` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const entries = performance.getEntriesByType("navigation");
entries.forEach((entry) => {
  const unloadEventTime = entry.unloadEventEnd - entry.unloadEventStart;
  if (unloadEventTime > 0) {
    console.log(`${entry.name}:
      load event handler time: ${unloadEventTime}ms`);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رویداد [`unload`](/en-US/docs/Web/API/Window/unload_event)