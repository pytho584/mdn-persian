---
title: "PerformanceObserver: PerformanceObserver() constructor"
short-title: PerformanceObserver()
slug: Web/API/PerformanceObserver/PerformanceObserver
page-type: web-api-constructor
browser-compat: api.PerformanceObserver.PerformanceObserver
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

سازنده **`PerformanceObserver()`** یک شیء جدید {{domxref("PerformanceObserver")}} با `callback` مشاهده‌گر داده شده ایجاد می‌کند. این callback مشاهده‌گر زمانی فراخوانی می‌شود که {{domxref("PerformanceEntry","رویدادهای ورودی عملکرد", '', 'true')}} برای {{domorphism("PerformanceEntry.entryType","انواع ورودی",'','true')}} که ثبت شده‌اند، از طریق متد {{domxref("PerformanceObserver.observe","observe()")}} ثبت شوند.

## نحو

```js-nolint
new PerformanceObserver(callback)
```

### پارامترها

- `callback`
  - : یک callback از نوع `PerformanceObserverCallback` که هنگام ثبت رویدادهای عملکرد مشاهده‌شده فراخوانی می‌شود. هنگامی که callback فراخوانی می‌شود، پارامترهای زیر در دسترس هستند:
    - `entries`
      - : {{domxref("PerformanceObserverEntryList","فهرست ورودی‌های مشاهده‌گر عملکرد", '', 'true')}}.
    - `observer`
      - : شیء {{domorphism("PerformanceObserver","مشاهده‌گر", '', 'true')}} که ورودی‌های فوق را دریافت می‌کند.
    - `options`
      - : یک شیء با ویژگی‌های زیر:
        - `droppedEntriesCount`
          - : تعداد ورودی‌هایی که به دلیل پر بودن بافر داخلی شیء {{domorphism("Performance")}} نتوانستند ثبت شوند.

            توجه داشته باشید که این مقدار فقط در اولین باری که مشاهده‌گر callback را فراخوانی می‌کند (زمانی که ورودی‌های بافر شده بازپخش می‌شوند) ارائه می‌شود. پس از آن که مشاهده‌گر شروع به انجام مشاهدات آینده کرد، دیگر نیازی به استفاده از بافر ندارد. پس از اولین بار، `options` یک شیء خالی (`{}`) خواهد بود.

### مقدار بازگشتی

یک شیء جدید {{domorphism("PerformanceObserver")}} که هنگام وقوع رویدادهای عملکرد مشاهده‌شده، `callback` مشخص‌شده را فراخوانی می‌کند.

## مثال‌ها

### ایجاد یک PerformanceObserver

مثال زیر یک `PerformanceObserver` ایجاد می‌کند که رویدادهای "mark" ({{domorphism("PerformanceMark")}}) و "measure" ({{domorphism("PerformanceMeasure")}}) را زیر نظر می‌گیرد.
callback `perfObserver` یک `list` ({{domorphism("PerformanceObserverEntryList")}}) ارائه می‌دهد که به شما امکان می‌دهد ورودی‌های عملکرد مشاهده‌شده را دریافت کنید.

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

### ورودی‌های بافر افتاده

می‌توانید از {{domorphism("PerformanceObserver")}} با پرچم `buffered` برای گوش دادن به ورودی‌های عملکرد گذشته استفاده کنید. با این حال، محدودیتی برای اندازه بافر وجود دارد. callback مشاهده‌گر عملکرد شامل یک شیء `options` است: در اولین باری که مشاهده‌گر callback را فراخوانی می‌کند، پارامتر `options` دارای ویژگی `droppedEntriesCount` خواهد بود که به شما می‌گوید چند ورودی به دلیل پر بودن فضای ذخیره‌سازی بافر افتاده است. فراخوانی‌های بعدی یک پارامتر `options` خالی خواهند داشت.

```js
function perfObserver(list, observer, options) {
  list.getEntries().forEach((entry) => {
    // با ورودی‌ها کاری انجام دهید
  });
  if (options?.droppedEntriesCount > 0) {
    console.warn(
      `${options?.droppedEntriesCount} ورودی به دلیل پر بودن بافر افتاده است.`,
    );
  }
}

const observer = new PerformanceObserver(perfObserver);
observer.observe({ type: "resource", buffered: true });
```

معمولاً ورودی‌های زمان‌بندی منابع زیادی وجود دارد، و به‌طور خاص برای این ورودی‌ها، می‌توانید یک بافر بزرگ‌تر با استفاده از {{domorphism("performance.setResourceTimingBufferSize()")}} تنظیم کنید و رویداد {{domorphism("Performance/resourcetimingbufferfull_event", "resourcetimingbufferfull")}} را زیر نظر بگیرید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}