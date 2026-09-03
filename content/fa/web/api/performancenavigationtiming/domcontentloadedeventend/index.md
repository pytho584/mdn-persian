---
title: "PerformanceNavigationTiming: domContentLoadedEventEnd property"
short-title: domContentLoadedEventEnd
slug: Web/API/PerformanceNavigationTiming/domContentLoadedEventEnd
page-type: web-api-instance-property
browser-compat: api.PerformanceNavigationTiming.domContentLoadedEventEnd
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`domContentLoadedEventEnd`** یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که زمان بلافاصله پس از اتمام اجرای مدیریت‌کننده رویداد [`DOMContentLoaded`](/en-US/docs/Web/API/Document/DOMContentLoaded_event) سند فعلی را نشان می‌دهد.

معمولاً فریمورک‌ها و کتابخانه‌ها قبل از شروع به اجرای کد خود منتظر رویداد `DOMContentLoaded` می‌مانند. می‌توانیم از ویژگی‌های `domContentLoadedEventEnd` و [`domContentLoadedEventStart`](/en-US/docs/Web/API/PerformanceNavigationTiming/domContentLoadedEventStart) برای محاسبه مدت زمانی که این کار طول می‌کشد استفاده کنیم.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} که زمان بلافاصله پس از اتمام اجرای مدیریت‌کننده رویداد [`DOMContentLoaded`](/en-US/docs/Web/API/Document/DOMContentLoaded_event) سند فعلی را نشان می‌دهد.

## مثال‌ها

### اندازه‌گیری زمان اجرای مدیریت‌کننده رویداد `DOMContentLoaded`

از ویژگی `domContentLoadedEventEnd` می‌توان برای اندازه‌گیری مدت زمان پردازش مدیریت‌کننده رویداد [`DOMContentLoaded`](/en-US/docs/Web/API/Document/DOMContentLoaded_event) استفاده کرد.

مثال با استفاده از {{domxref("PerformanceObserver")}}، که ورودی‌های عملکرد `navigation` جدید را هنگام ثبت شدن در خط زمانی عملکرد مرورگر اطلاع‌رسانی می‌کند. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

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

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `navigation` موجود در خط زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

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