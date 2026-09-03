---
title: "PeriodicSyncManager: unregister() method"
short-title: unregister()
slug: Web/API/PeriodicSyncManager/unregister
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PeriodicSyncManager.unregister
---

{{APIRef("Periodic Background Sync")}}{{SeeCompatTable}}{{AvailableInWorkers}}

متد **`unregister()`** از رابط {{domxref("PeriodicSyncManager")}} درخواست همگام‌سازی دوره‌ایِ متناظر با برچسب (tag) مشخص‌شده را لغو ثبت می‌کند و یک {{jsxref('Promise')}} برمی‌گرداند که وقتی فرایند لغو ثبت کامل شد، resolve می‌شود.

## نحو

```js-nolint
unregister(tag)
```

### پارامترها

- `tag`
  - : یک {{jsxref('String')}} یکتا که همگام‌سازی پس‌زمینهٔ مورد نظر را توصیف می‌کند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} برمی‌گرداند که با {{jsxref('undefined')}} resolve می‌شود.

### استثناها

هیچ‌کدام.

## مثال‌ها

مثال زیر یک همگام‌سازی دوره‌ای را حذف می‌کند تا از همگام‌سازی مقاله‌ها در پس‌زمینه جلوگیری شود:

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

- [تجربه‌های آفلاین غنی‌تر با Periodic Background Sync API](https://developer.chrome.com/docs/capabilities/periodic-background-sync)