---
title: "PerformanceObserverEntryList: getEntriesByType() method"
short-title: getEntriesByType()
slug: Web/API/PerformanceObserverEntryList/getEntriesByType
page-type: web-api-instance-method
browser-compat: api.PerformanceObserverEntryList.getEntriesByType
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`getEntriesByType()`** از {{domxref("PerformanceObserverEntryList")}} فهرستی از اشیای {{domxref("PerformanceEntry","ورودی عملکرد", '', 'true')}} را که به‌طور صریح _مشاهده شده‌اند_، برای یک {{domxref("PerformanceEntry.entryType","نوع ورودی عملکرد", '', 'true')}} مشخص بازمی‌گرداند. اعضای این فهرست بر اساس مجموعه‌ای از {{domxref("PerformanceEntry.entryType","انواع ورودی", '', 'true')}} تعیین می‌شوند که در فراخوانی متد {{domxref("PerformanceObserver.observe","observe()")}} مشخص شده‌اند. این فهرست در تابع callback ناظر (به‌عنوان اولین پارامتر callback) در دسترس است.

## نحو (Syntax)

```js-nolint
getEntriesByType(type)
```

### پارامترها

- `type`
  - : نوع ورودی مورد نظر برای بازیابی، مانند `"mark"`. انواع ورودی معتبر در {{domxref("PerformanceEntry.entryType")}} فهرست شده‌اند.

### مقدار بازگشتی

فهرستی از اشیای {{domxref("PerformanceEntry")}} که به‌طور صریح _مشاهده شده‌اند_ و دارای `type` مشخص‌شده هستند. اقلام به ترتیب زمانی بر اساس {{domxref("PerformanceEntry.startTime","startTime")}} ورودی‌ها مرتب می‌شوند. اگر هیچ شیئی با `type` مشخص‌شده وجود نداشته باشد، یا آرگومانی ارائه نشود، یک فهرست خالی بازگردانده می‌شود.

## مثال‌ها

### کار با getEntries، getEntriesByName و getEntriesByType

مثال زیر تفاوت بین متدهای {{domxref("PerformanceObserverEntryList.getEntries", "getEntries()")}}، {{domxref("PerformanceObserverEntryList.getEntriesByName", "getEntriesByName()")}} و `getEntriesByType()` را نشان می‌دهد.

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

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر (Browser compatibility)

{{Compat}}