---
title: "PeriodicSyncManager: getTags() method"
short-title: getTags()
slug: Web/API/PeriodicSyncManager/getTags
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PeriodicSyncManager.getTags
---

{{APIRef("Periodic Background Sync")}}{{SeeCompatTable}}{{AvailableInWorkers}}

متد **`getTags()`** از رابط {{domxref("PeriodicSyncManager")}} یک {{jsxref('Promise')}} برمی‌گرداند که با فهرستی از آبجکت‌های {{jsxref('String')}} resolve می‌شود؛ این فهرست برچسب‌هایی را نشان می‌دهد که در حال حاضر برای همگام‌سازی دوره‌ای ثبت شده‌اند.

## دستور زبان

```js-nolint
getTags()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که به فهرستی از آبجکت‌های {{jsxref('String')}} resolve می‌شود و برچسب‌هایی را نشان می‌دهد که در حال حاضر برای همگام‌سازی دوره‌ای ثبت شده‌اند.

### استثناها

هیچ.

## مثال‌ها

مثال زیر از متد `getTags()` استفاده می‌کند تا بررسی کند آیا کار همگام‌سازی دوره‌ای با یک برچسب مشخص ثبت شده است یا خیر.

```js
navigator.serviceWorker.ready.then((registration) => {
  registration.periodicSync.getTags().then((tags) => {
    if (tags.includes("get-latest-news")) skipDownloadingLatestNewsOnPageLoad();
  });
});
```

`skipDownloadingLatestNewsOnPageLoad()` یک تابع تعریف‌شده توسط توسعه‌دهنده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [تجربه‌های آفلاین غنی‌تر با Periodic Background Sync API](https://developer.chrome.com/docs/capabilities/periodic-background-sync)