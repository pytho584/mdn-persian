---
title: "PeriodicSyncEvent: tag property"
short-title: tag
slug: Web/API/PeriodicSyncEvent/tag
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PeriodicSyncEvent.tag
---

{{APIRef("Periodic Background Sync")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنی **`tag`** در رابط {{domxref("PeriodicSyncEvent")}}، شناسه‌ای را برمی‌گرداند که توسعه‌دهنده برای {{domxref('PeriodicSyncEvent')}} تعریف کرده است. این شناسه هنگام فراخوانی متد {{domxref('PeriodicSyncManager.register()')}} از رابط {{domxref('PeriodicSyncManager')}} مشخص می‌شود. برنامه وب می‌تواند از چندین برچسب استفاده کند تا کارهای دوره‌ای متفاوتی را با فرکانس‌های مختلف اجرا کند.

## مقدار

یک {{jsxref('String')}} شامل شناسه تعریف‌شده را برمی‌گرداند.

## مثال‌ها

مثال زیر نحوه گوش دادن به رویداد همگام‌سازی دوره‌ای در سرویس‌ورکر و دسترسی به ویژگی `tag` را نشان می‌دهد.

```js
self.addEventListener("periodicsync", (event) => {
  console.log(event.tag); // logs the events tag
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [تجربه‌های آفلاین غنی‌تر با Periodic Background Sync API](https://developer.chrome.com/docs/capabilities/periodic-background-sync)