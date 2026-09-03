---
title: "Performance: getEntries() method"
short-title: getEntries()
slug: Web/API/Performance/getEntries
page-type: web-api-instance-method
browser-compat: api.Performance.getEntries
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`getEntries()`** یک آرایه از تمام اشیاء {{domxref("PerformanceEntry")}} که در حال حاضر در timeline عملکرد وجود دارند، برمی‌گرداند.

اگر فقط به ورودی‌های عملکرد از انواع خاص یا با نام‌های خاص علاقه‌مندید، به {{domxref("Performance.getEntriesByType", "getEntriesByType()")}} و {{domxref("Performance.getEntriesByName", "getEntriesByName()")}} مراجعه کنید.

> [!NOTE]
> این متد شما را از ورودی‌های جدید عملکرد مطلع نمی‌کند؛ شما فقط ورودی‌هایی را دریافت می‌کنید که در زمان فراخوانی این متد در timeline عملکرد وجود دارند.
> برای دریافت اعلان‌ها درباره ورودی‌ها به محض در دسترس شدن، از یک {{domxref("PerformanceObserver")}} استفاده کنید.

انواع ورودی زیر به هیچ وجه توسط این متد پشتیبانی نمی‌شوند و حتی اگر ورودی‌هایی برای این انواع وجود داشته باشند، بازگردانده نخواهند شد:

- `"element"` ({{domxref("PerformanceElementTiming")}})
- `"event"` ({{domxref("PerformanceEventTiming")}})
- `"largest-contentful-paint"` ({{domxref("LargestContentfulPaint")}})
- `"layout-shift"` ({{domxref("LayoutShift")}})
- `"longtask"` ({{domxref("PerformanceLongTaskTiming")}})

برای دسترسی به ورودی‌های این انواع، باید به جای آن از {{domxref("PerformanceObserver")}} استفاده کنید.

## Syntax

```js-nolint
getEntries()
```

### Parameters

هیچ.

### Return value

یک {{jsxref("Array")}} از اشیاء {{domxref("PerformanceEntry")}}. موارد به ترتیب زمانی بر اساس {{domxref("PerformanceEntry.startTime","startTime")}} ورودی‌ها قرار خواهند گرفت.

## Examples

### ثبت تمام نشانگرها و اندازه‌گیری‌های عملکرد

با فرض اینکه اشیاء {{domxref("PerformanceMark")}} و {{domxref("PerformanceMeasure")}} خود را در مکان‌های مناسب کد خود ایجاد کرده‌اید، ممکن است بخواهید همه آنها را به صورت زیر در کنسول ثبت کنید:

```js
// Example markers/measures
performance.mark("login-started");
performance.mark("login-finished");
performance.mark("form-sent");
performance.mark("video-loaded");
performance.measure("login-duration", "login-started", "login-finished");

const entries = performance.getEntries();

entries.forEach((entry) => {
  if (entry.entryType === "mark") {
    console.log(`${entry.name}'s startTime: ${entry.startTime}`);
  }
  if (entry.entryType === "measure") {
    console.log(`${entry.name}'s duration: ${entry.duration}`);
  }
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Performance.getEntriesByType()")}}
- {{domxref("Performance.getEntriesByName()")}}