---
title: PerformanceObserver
slug: Web/API/PerformanceObserver
page-type: web-api-interface
browser-compat: api.PerformanceObserver
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

اینترفیس **`PerformanceObserver`** برای مشاهده رویدادهای اندازه‌گیری عملکرد و اطلاع‌یافتن از {{domxref("PerformanceEntry","ورودی‌های عملکرد", '', 'true')}} جدید به محض ثبت‌شدن در _خط زمانی عملکرد_ مرورگر استفاده می‌شود.

## سازنده

- {{domxref("PerformanceObserver.PerformanceObserver","PerformanceObserver()")}}
  - : یک شیء جدید `PerformanceObserver` ایجاد و برمی‌گرداند.

## ویژگی‌های ایستا

- {{domxref("PerformanceObserver.supportedEntryTypes_static", "PerformanceObserver.supportedEntryTypes")}} {{ReadOnlyInline}}
  - : آرایه‌ای از مقادیر {{domxref("PerformanceEntry.entryType","entryType")}} که توسط عامل کاربر پشتیبانی می‌شوند را برمی‌گرداند.

## روش‌های نمونه

- {{domxref("PerformanceObserver.observe","PerformanceObserver.observe()")}}
  - : مجموعه انواع ورودی‌هایی که باید مشاهده شوند را مشخص می‌کند. تابع callback ناظر عملکرد زمانی فراخوانی می‌شود که یک ورودی عملکرد برای یکی از `entryType`های مشخص‌شده ثبت شود.
- {{domxref("PerformanceObserver.disconnect","PerformanceObserver.disconnect()")}}
  - : دریافت ورودی‌های عملکرد توسط callback ناظر عملکرد را متوقف می‌کند.
- {{domxref("PerformanceObserver.takeRecords","PerformanceObserver.takeRecords()")}}
  - : فهرست فعلی ورودی‌های عملکرد ذخیره‌شده در ناظر عملکرد را برمی‌گرداند و آن را خالی می‌کند.

## مثال‌ها

### ایجاد یک PerformanceObserver

مثال زیر یک `PerformanceObserver` ایجاد می‌کند که رویدادهای "mark" ({{domxref("PerformanceMark")}}) و "measure" ({{domxref("PerformanceMeasure")}}) را تماشا می‌کند.
تابع callback یعنی `perfObserver` یک `list` ({{domxref("PerformanceObserverEntryList")}}) ارائه می‌دهد که به شما امکان می‌دهد ورودی‌های عملکرد مشاهده‌شده را دریافت کنید.

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

## همچنین ببینید

- {{domxref('MutationObserver')}}
- {{domxref('ResizeObserver')}}
- {{domxref('IntersectionObserver')}}