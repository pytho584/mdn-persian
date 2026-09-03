---
title: PerformanceObserverEntryList
slug: Web/API/PerformanceObserverEntryList
page-type: web-api-interface
browser-compat: api.PerformanceObserverEntryList
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

اینترفیس **`PerformanceObserverEntryList`** فهرستی از {{domxref("PerformanceEntry","رویدادهای کارایی", '', 'true')}} است که به‌طور صریح از طریق متد {{domxref("PerformanceObserver.observe","observe()")}} مشاهده شده‌اند.

## روش‌های نمونه

- {{domxref("PerformanceObserverEntryList.getEntries","PerformanceObserverEntryList.getEntries()")}}
  - : فهرستی از تمام اشیاء {{domxref("PerformanceEntry")}} که به‌طور صریح مشاهده شده‌اند را برمی‌گرداند.
- {{domxref("PerformanceObserverEntryList.getEntriesByType","PerformanceObserverEntryList.getEntriesByType()")}}
  - : فهرستی از تمام اشیاء {{domxref("PerformanceEntry")}} که به‌طور صریح مشاهده شده‌اند و دارای نوع ورودی مشخص‌شده هستند را برمی‌گرداند.
- {{domxref("PerformanceObserverEntryList.getEntriesByName","PerformanceObserverEntryList.getEntriesByName()")}}
  - : فهرستی از تمام اشیاء {{domxref("PerformanceEntry")}} که به‌طور صریح مشاهده شده‌اند و بر اساس نام و نوع ورودی داده‌شده هستند را برمی‌گرداند.

## مثال

### استفاده از PerformanceObserverEntryList

در مثال زیر، `list` شیء `PerformanceObserverEntryList` است. متد {{domxref("PerformanceObserverEntryList.getEntries","getEntries()")}} فراخوانی می‌شود تا تمام اشیاء {{domxref("PerformanceEntry")}} که به‌طور صریح مشاهده شده‌اند و در این مورد «measure» و «mark» هستند، دریافت شوند.

```js
function perfObserver(list, observer) {
  list.getEntries().forEach((entry) => {
    if (entry.entryType === "mark") {
      console.log(`${entry.name}'s startTime: ${entry.startTime}`);
    }
    if (entry.entryType === "measure") {
      console.log(`${entry.name}'s duration: ${entry.duration}`);
    }
  });
}
const observer = new PerformanceObserver(perfObserver);
observer.observe({ entryTypes: ["measure", "mark"] });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}