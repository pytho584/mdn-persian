---
title: PeriodicSyncManager
slug: Web/API/PeriodicSyncManager
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PeriodicSyncManager
---

{{APIRef("Periodic Background Sync")}}{{SeeCompatTable}}{{AvailableInWorkers}}

رابطِ **`PeriodicSyncManager`** از {{domxref('Web Periodic Background Synchronization API', '', '', 'nocode')}} راهی برای ثبت کارهایی فراهم می‌کند که باید در یک service worker در بازه‌های زمانی متناوب و هنگام برقراری اتصال شبکه اجرا شوند. به این کارها، درخواست‌های همگام‌سازی دوره‌ای در پس‌زمینه گفته می‌شود. از طریق {{domxref('ServiceWorkerRegistration.periodicSync')}} می‌توانید به `PeriodicSyncManager` دسترسی داشته باشید.

## ویژگی‌های نمونه

هیچ‌کدام.

## روش‌های نمونه

- {{domxref('PeriodicSyncManager.register()')}} {{Experimental_Inline}}
  - یک درخواست همگام‌سازی دوره‌ای را با برچسب (tag) و گزینه‌های مشخص‌شده در مرورگر ثبت می‌کند. یک {{jsxref('Promise')}} برمی‌گرداند که پس از تکمیل ثبت، resolve می‌شود.
- {{domxref('PeriodicSyncManager.getTags()')}} {{Experimental_Inline}}
  - یک {{jsxref('Promise')}} برمی‌گرداند که با فهرستی از {{jsxref('String','strings')}} («رشته‌ها») resolve می‌شود؛ این فهرست نشان‌دهندهٔ برچسب‌هایی است که در حال حاضر برای همگام‌سازی دوره‌ای ثبت شده‌اند.
- {{domxref('PeriodicSyncManager.unregister()')}} {{Experimental_Inline}}
  - درخواست همگام‌سازی دوره‌ای مربوط به برچسب مشخص‌شده را لغو ثبت می‌کند و یک {{jsxref('Promise')}} برمی‌گرداند که پس از تکمیل لغو ثبت، resolve می‌شود.

## مثال‌ها

مثال‌های زیر چگونگی استفاده از این رابط را نشان می‌دهند.

### درخواست یک همگام‌سازی دوره‌ای در پس‌زمینه

تابع ناهمگام زیر یک همگام‌سازی دوره‌ای در پس‌زمینه را با حداقل بازهٔ زمانی یک روز از یک بافت مرورگر (browsing context) ثبت می‌کند:

```js
async function registerPeriodicNewsCheck() {
  const registration = await navigator.serviceWorker.ready;
  try {
    await registration.periodicSync.register("get-latest-news", {
      minInterval: 24 * 60 * 60 * 1000,
    });
  } catch {
    console.log("Periodic Sync could not be registered!");
  }
}
```

### بررسی یک همگام‌سازی دوره‌ای در پس‌زمینه با برچسب

این کد بررسی می‌کند که آیا یک کار همگام‌سازی دوره‌ای در پس‌زمینه با برچسب معین ثبت شده است یا خیر.

```js
navigator.serviceWorker.ready.then((registration) => {
  registration.periodicSync.getTags().then((tags) => {
    if (tags.includes("get-latest-news")) skipDownloadingLatestNewsOnPageLoad();
  });
});
```

### حذف یک کار همگام‌سازی دوره‌ای در پس‌زمینه

کد زیر یک کار همگام‌سازی دوره‌ای در پس‌زمینه را حذف می‌کند تا مقاله‌ها دیگر در پس‌زمینه همگام‌سازی نشوند.

```js
navigator.serviceWorker.ready.then((registration) => {
  registration.periodicSync.unregister("get-latest-news");
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Richer offline experiences with the Periodic Background Sync API](https://developer.chrome.com/docs/capabilities/periodic-background-sync)