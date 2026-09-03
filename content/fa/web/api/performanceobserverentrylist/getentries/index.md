---
title: "PerformanceObserverEntryList: getEntries() method"
short-title: getEntries()
slug: Web/API/PerformanceObserverEntryList/getEntries
page-type: web-api-instance-method
browser-compat: api.PerformanceObserverEntryList.getEntries
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`getEntries()`** از رابط {{domxref("PerformanceObserverEntryList")}} یک لیست از اشیاء {{domxref("PerformanceEntry","ورودی عملکرد", '', 'true')}} که به طور صریح مشاهده شده‌اند، برمی‌گرداند. اعضای این لیست توسط مجموعه‌ای از {{domxref("PerformanceEntry.entryType","انواع ورودی", '', 'true')}} که در فراخوانی متد {{domxref("PerformanceObserver.observe","observe()")}} مشخص شده‌اند، تعیین می‌شوند. این لیست در تابع callback ناظر (به عنوان اولین پارامتر در callback) در دسترس است.

## Syntax

```js-nolint
getEntries()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک لیست از اشیاء {{domxref("PerformanceEntry")}} که به طور صریح مشاهده شده‌اند. آیتم‌ها به ترتیب زمانی بر اساس {{domxref("PerformanceEntry.startTime","startTime")}} ورودی‌ها مرتب خواهند شد. اگر هیچ شیئی یافت نشود، یک لیست خالی بازگردانده می‌شود.

## مثال‌ها

### کار با getEntries، getEntriesByName و getEntriesByType

مثال زیر تفاوت بین متدهای `getEntries()`، {{domxref("PerformanceObserverEntryList.getEntriesByName", "getEntriesByName()")}} و {{domxref("PerformanceObserverEntryList.getEntriesByType", "getEntriesByType()")}} را نشان می‌دهد.

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

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}