---
title: "Performance: getEntriesByName() method"
short-title: getEntriesByName()
slug: Web/API/Performance/getEntriesByName
page-type: web-api-instance-method
browser-compat: api.Performance.getEntriesByName
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`getEntriesByName()`** آرایه‌ای از اشیای {{domxref("PerformanceEntry")}} را برمی‌گرداند که در حال حاضر در خط زمانی عملکرد (performance timeline) با نام و نوع داده شده وجود دارند.

اگر به ورودی‌های عملکرد از انواع خاصی علاقه‌مندید، به {{domxref("Performance.getEntriesByType", "getEntriesByType()")}} مراجعه کنید. برای همه ورودی‌های عملکرد، {{domxref("Performance.getEntries", "getEntries()")}} را ببینید.

> [!NOTE]
> این متد شما را از ورودی‌های جدید عملکرد مطلع نمی‌کند؛ شما فقط ورودی‌هایی را دریافت می‌کنید که در زمان فراخوانی این متد در خط زمانی عملکرد وجود دارند. برای دریافت اعلان‌ها درباره ورودی‌ها به محض در دسترس شدن، از یک {{domxref("PerformanceObserver")}} استفاده کنید.

انواع ورودی زیر توسط این متد اصلاً پشتیبانی نمی‌شوند و حتی اگر ورودی‌هایی برای این انواع وجود داشته باشد، بازگردانده نخواهند شد:

- `"element"` ({{domxref("PerformanceElementTiming")}})
- `"event"` ({{domxref("PerformanceEventTiming")}})
- `"largest-contentful-paint"` ({{domxref("LargestContentfulPaint")}})
- `"layout-shift"` ({{domxref("LayoutShift")}})
- `"longtask"` ({{domxref("PerformanceLongTaskTiming")}})

برای دسترسی به ورودی‌های این انواع، باید به جای آن از یک {{domxref("PerformanceObserver")}} استفاده کنید.

## Syntax

```js-nolint
getEntriesByName(name)
getEntriesByName(name, type)
```

### Parameters

- `name`
  - : نام ورودی‌هایی که باید بازیابی شوند.
- `type` {{optional_inline}}
  - : نوع ورودی‌هایی که باید بازیابی شوند، مانند `"mark"`. انواع معتبر ورودی در {{domxref("PerformanceEntry.entryType")}} فهرست شده‌اند.

### Return value

یک {{jsxref("Array")}} از اشیای {{domxref("PerformanceEntry")}} که دارای `name` و `type` مشخص شده هستند. موارد به ترتیب زمانی بر اساس {{domxref("PerformanceEntry.startTime","startTime")}} ورودی‌ها مرتب خواهند شد. اگر هیچ شیئی با معیارهای مشخص شده مطابقت نداشته باشد، یک آرایه خالی بازگردانده می‌شود.

## Examples

### ثبت نشانگرهای عملکرد

مثال زیر همه اشیای {{domxref("PerformanceMark")}} به نام `"debug-mark"` را ثبت می‌کند.

```js
const debugMarks = performance.getEntriesByName("debug-mark", "mark");
debugMarks.forEach((entry) => {
  console.log(`${entry.name}'s startTime: ${entry.startTime}`);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Performance.getEntries()")}}
- {{domxref("Performance.getEntriesByType()")}}