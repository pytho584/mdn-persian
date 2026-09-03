---
title: "PerformanceNavigationTiming: domContentLoadedEventStart property"
short-title: domContentLoadedEventStart
slug: Web/API/PerformanceNavigationTiming/domContentLoadedEventStart
page-type: web-api-instance-property
browser-compat: api.PerformanceNavigationTiming.domContentLoadedEventStart
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`domContentLoadedEventStart`** یک {{domxref("DOMHighResTimeStamp")}} را برمی‌گرداند که زمان دقیقاً قبل از شروع اجرای مدیریت‌کننده رویداد [`DOMContentLoaded`](/en-US/docs/Web/API/Document/DOMContentLoaded_event) سند فعلی را نشان می‌دهد.

معمولاً فریمورک‌ها و کتابخانه‌ها منتظر رویداد `DOMContentLoaded` می‌مانند تا اجرای کد خود را آغاز کنند. می‌توانیم از ویژگی‌های `domContentLoadedEventStart` و [`domContentLoadedEventEnd`](/en-US/docs/Web/API/PerformanceNavigationTiming/domContentLoadedEventEnd) برای محاسبه مدت زمانی که این اجرا طول می‌کشد استفاده کنیم.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} که زمان دقیقاً قبل از شروع اجرای مدیریت‌کننده رویداد [`DOMContentLoaded`](/en-US/docs/Web/API/Document/DOMContentLoaded_event) سند فعلی را نشان می‌دهد.

## مثال‌ها

### اندازه‌گیری زمان اجرای مدیریت‌کننده رویداد `DOMContentLoaded`

ویژگی `domContentLoadedEventStart` می‌تواند برای اندازه‌گیری مدت زمانی که برای پردازش مدیریت‌کننده رویداد [`DOMContentLoaded`](/en-US/docs/Web/API/Document/DOMContentLoaded_event) لازم است استفاده شود.

مثال با استفاده از {{domxref("PerformanceObserver")}}، که با ثبت ورودی‌های جدید عملکرد از نوع `navigation` در جدول زمانی عملکرد مرورگر، آن‌ها را اطلاع‌رسانی می‌کند. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const domContentLoadedTime =
      entry.domContentLoadedEventEnd - entry.domContentLoadedEventStart;
    console.log(
      `${entry.name}: DOMContentLoaded processing time: ${domContentLoadedTime}ms`,
    );
  });
});

observer.observe({ type: "navigation", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `navigation` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const entries = performance.getEntriesByType("navigation");
entries.forEach((entry) => {
  const domContentLoadedTime =
    entry.domContentLoadedEventEnd - entry.domContentLoadedEventStart;
  console.log(
    `${entry.name}: DOMContentLoaded processing time: ${domContentLoadedTime}ms`,
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [DOMContentLoaded](/en-US/docs/Web/API/Document/DOMContentLoaded_event)