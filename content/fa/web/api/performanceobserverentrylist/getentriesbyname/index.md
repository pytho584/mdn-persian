---
title: "PerformanceObserverEntryList: getEntriesByName() method"
short-title: getEntriesByName()
slug: Web/API/PerformanceObserverEntryList/getEntriesByName
page-type: web-api-instance-method
browser-compat: api.PerformanceObserverEntryList.getEntriesByName
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`getEntriesByName()`** از رابط {{domxref("PerformanceObserverEntryList")}} فهرستی از اشیاء {{domxref("PerformanceEntry")}} را که به‌طور مشخص مشاهده شده‌اند، برای یک {{domxref("PerformanceEntry.name","name")}} و {{domxref("PerformanceEntry.entryType","entryType")}} معین برمی‌گرداند. اعضای این فهرست بر اساس مجموعه‌ای از «نوع‌های ورودی» (entry types) مشخص‌شده در فراخوانی متد {{domxref("PerformanceObserver.observe","observe()")}} تعیین می‌شوند. این فهرست در تابع callback ناظر (به‌عنوان پارامتر اول در callback) در دسترس است.

## Syntax

```js-nolint
getEntriesByName(name)
getEntriesByName(name, type)
```

### پارامترها

- `name`
  - : یک رشته (string) که نام ورودی مورد نظر برای بازیابی را مشخص می‌کند.
- `type` {{optional_inline}}
  - : یک رشته که نوع ورودی مورد نظر برای بازیابی را مشخص می‌کند، مانند `"mark"`. انواع ورودی معتبر در {{domxref("PerformanceEntry.entryType")}} فهرست شده‌اند.

### مقدار بازگشتی

فهرستی از اشیاء {{domxref("PerformanceEntry","performance entry", '', 'true')}} که به‌طور مشخص _مشاهده شده_ و دارای `name` و `type` مشخص‌شده هستند. اگر آرگومان `type` مشخص نشود، فقط `name` برای تعیین ورودی‌های بازگشتی استفاده می‌شود. موارد به ترتیب زمانی بر اساس {{domxref("PerformanceEntry.startTime","startTime")}} ورودی‌ها مرتب می‌شوند. اگر هیچ شیئی معیارهای مشخص‌شده را برآورده نکند، یک فهرست خالی بازگردانده می‌شود.

## مثال‌ها

### کار با getEntries، getEntriesByName و getEntriesByType

مثال زیر تفاوت بین متدهای {{domxref("PerformanceObserverEntryList.getEntries", "getEntries()")}}، `getEntriesByName()` و {{domxref("PerformanceObserverEntryList.getEntriesByType", "getEntriesByType()")}} را نشان می‌دهد.

```js
const observer = new PerformanceObserver((list, obs) => {
  // Log all entries
  let perfEntries = list.getEntries();
  perfEntries.forEach((entry) => {
    console.log(`${entry.name}'s duration: ${entry.duration}`);
  });

  // Log entries named "debugging" with type "measure"
  perfEntries = list.getEntriesByName("debugging", "measure");
  perfEntries.forEach((entry) => {
    console.log(`${entry.name}'s duration: ${entry.duration}`);
  });

  // Log entries with type "mark"
  perfEntries = list.getEntriesByType("mark");
  perfEntries.forEach((entry) => {
    console.log(`${entry.name}'s startTime: ${entry.startTime}`);
  });
});

// Subscribe to various performance event types
observer.observe({
  entryTypes: ["mark", "measure", "navigation", "resource"],
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}