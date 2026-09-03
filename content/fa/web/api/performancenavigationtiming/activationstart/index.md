---
title: "PerformanceNavigationTiming: activationStart property"
short-title: activationStart
slug: Web/API/PerformanceNavigationTiming/activationStart
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceNavigationTiming.activationStart
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`activationStart`** نشان‌دهندهٔ مدت زمان بین شروع پیش‌رندر کردن یک سند و فعال‌سازی آن است.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} که مدت زمان بین شروع پیش‌رندر کردن سند و فعال‌سازی را به میلی‌ثانیه نشان می‌دهد.

اگر صفحه پیش‌رندر نشده باشد یا هنوز در حال پیش‌رندر باشد، مقدار `0` است.

## مثال‌ها

### تشخیص صفحات پیش‌رندر شده

هنگامی که یک سند پیش‌رندر شده فعال می‌شود، `activationStart` به زمان فعلی تنظیم می‌شود. تابع زیر می‌تواند بررسی کند که آیا یک صفحه در حال {{DOMxRef("Document.prerendering","پیش‌رندر")}} است یا قبلاً پیش‌رندر شده است:

```js
function pagePrerendered() {
  return (
    document.prerendering ||
    self.performance?.getEntriesByType?.("navigation")[0]?.activationStart > 0
  );
}
```

### اندازه‌گیری نقاط عطف عملکرد درک‌شده توسط کاربر

با صفحات پیش‌رندر شده، ممکن است یک صفحه مدت‌ها قبل از مراجعهٔ واقعی به آن ایجاد شده باشد. هنگام استفاده از [Performance API](/en-US/docs/Web/API/Performance_API) در صفحات پیش‌رندر شده، مقایسهٔ مقادیر بازگشتی با `activationStart` ضروری است تا از اندازه‌گیری‌های گمراه‌کننده جلوگیری شود.

```js
// زمان تا لحظهٔ فعال‌سازی
let activationStart =
  performance.getEntriesByType("navigation")[0].activationStart;

// زمان تا اولین نمایش (first paint)
let firstPaint = performance.getEntriesByName("first-paint")[0].startTime;

// زمان تا اولین نمایش محتوایی (first contentful paint)
let firstContentfulPaint = performance.getEntriesByName(
  "first-contentful-paint",
)[0].startTime;

console.log(`زمان تا اولین نمایش: ${firstPaint - activationStart}`);
console.log(
  `زمان تا اولین نمایش محتوایی: ${firstContentfulPaint - activationStart}`,
);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Speculation Rules API](/en-US/docs/Web/API/Speculation_Rules_API)
- [بارگذاری حدسی (Speculative loading)](/en-US/docs/Web/Performance/Guides/Speculative_loading)