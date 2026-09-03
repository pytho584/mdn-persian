---
title: "Performance: getEntriesByType() method"
short-title: getEntriesByType()
slug: Web/API/Performance/getEntriesByType
page-type: web-api-instance-method
browser-compat: api.Performance.getEntriesByType
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`getEntriesByType()`** یک آرایه از اشیاء {{domxref("PerformanceEntry")}} که در حال حاضر در زمان‌نمای عملکرد (performance timeline) برای یک _نوع_ مشخص وجود دارند، بازمی‌گرداند.

اگر به ورودی‌های عملکرد با نام خاصی علاقه‌مندید، به {{domxref("Performance.getEntriesByName", "getEntriesByName()")}} مراجعه کنید. برای همهٔ ورودی‌های عملکرد، {{domxref("Performance.getEntries", "getEntries()")}} را ببینید.

> [!NOTE]
> این متد شما را از ورودی‌های جدید عملکرد مطلع نمی‌کند؛ شما فقط ورودی‌هایی را دریافت می‌کنید که در زمان فراخوانی این متد در زمان‌نمای عملکرد وجود دارند. برای دریافت اعلان‌ها در مورد ورودی‌ها به محض در دسترس شدن، از یک {{domxref("PerformanceObserver")}} استفاده کنید.

انواع ورودی زیر به هیچ‌وجه توسط این متد پشتیبانی نمی‌شوند و حتی اگر ورودی‌هایی برای این انواع وجود داشته باشند، بازگردانده نمی‌شوند:

- `"element"` ({{domxref("PerformanceElementTiming")}})
- `"event"` ({{domxref("PerformanceEventTiming")}})
- `"largest-contentful-paint"` ({{domxref("LargestContentfulPaint")}})
- `"layout-shift"` ({{domxref("LayoutShift")}})
- `"longtask"` ({{domxref("PerformanceLongTaskTiming")}})

برای دسترسی به ورودی‌های این انواع، باید به جای آن از یک {{domxref("PerformanceObserver")}} استفاده کنید.

## نحو (Syntax)

```js-nolint
getEntriesByType(type)
```

### پارامترها

- `type`
  - : نوع ورودی که باید بازیابی شود، مانند `"mark"`. انواع ورودی معتبر در {{domxref("PerformanceEntry.entryType")}} فهرست شده‌اند. `entryTypes`های پشتیبانی‌شده را می‌توان با استفاده از ویژگی ایستا {{domxref("PerformanceObserver.supportedEntryTypes_static", "PerformanceObserver.supportedEntryTypes")}} به دست آورد.

### مقدار بازگشتی

یک {{jsxref("Array")}} از اشیاء {{domxref("PerformanceEntry")}} که دارای `type` مشخص شده هستند. آیتم‌ها به ترتیب زمانی بر اساس {{domxref("PerformanceEntry.startTime","startTime")}} ورودی‌ها خواهند بود. اگر هیچ شیئی دارای `type` مشخص شده نباشد، یا آرگومانی ارائه نشود، یک آرایه خالی بازگردانده می‌شود.

## مثال‌ها

### ثبت ورودی‌های منبع

مثال زیر همهٔ ورودی‌های با نوع `"resource"` را ثبت می‌کند.

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  console.log(`${entry.name}'s startTime: ${entry.startTime}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Performance.getEntries()")}}
- {{domxref("Performance.getEntriesByName()")}}
- {{domxref("PerformanceObserver.supportedEntryTypes_static", "PerformanceObserver.supportedEntryTypes")}}