---
title: "PerformanceNavigationTiming: unloadEventStart property"
short-title: unloadEventStart
slug: Web/API/PerformanceNavigationTiming/unloadEventStart
page-type: web-api-instance-property
browser-compat: api.PerformanceNavigationTiming.unloadEventStart
---

{{APIRef("Performance API")}}

خاصیتِ فقط‌خواندنی **`unloadEventStart`** یک {{domxref("DOMHighResTimeStamp")}} را برمی‌گرداند که نمایانگر زمان دقیقاً قبل از شروع اجرای کنترل‌کنندهٔ رویداد [`unload`](/en-US/docs/Web/API/Window/unload_event) سند قبلی است.

## مقدار

خاصیت `unloadEventStart` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp")}} که نمایانگر زمان دقیقاً قبل از شروع اجرای کنترل‌کنندهٔ رویداد [`unload`](/en-US/docs/Web/API/Window/unload_event) سند قبلی است.
- اگر سند قبلی وجود نداشته باشد، مقدار `0`.
- اگر صفحهٔ قبلی در یک مبدأ (origin) دیگر باشد، مقدار `0`.

## مثال‌ها

### اندازه‌گیری زمان اجرای کنترل‌کنندهٔ رویداد `unload`

خاصیت `unloadEventStart` می‌تواند برای اندازه‌گیری مدت زمان پردازش کنترل‌کنندهٔ رویداد [`unload`](/en-US/docs/Web/API/Window/unload_event) استفاده شود.

این ویژگی برای اندازه‌گیری زمان اجرای کنترل‌کننده‌های رویداد [`unload`](/en-US/docs/Web/API/Window/load_event) طولانی‌مدت مفید است.

```js
window.addEventListener("unload", (event) => {
  // Some long running code
});
```

مثال با استفاده از {{domxref("PerformanceObserver")}}، که هنگام ثبت ورودی‌های عملکرد `navigation` در جدول زمانی عملکرد مرورگر، آن‌ها را اطلاع‌رسانی می‌کند. از گزینهٔ `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

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

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `navigation` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد [`unload`](/en-US/docs/Web/API/Window/unload_event)