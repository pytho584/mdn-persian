---
title: "PeriodicSyncManager: register() method"
short-title: register()
slug: Web/API/PeriodicSyncManager/register
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PeriodicSyncManager.register
---

{{APIRef("Periodic Background Sync")}}{{SeeCompatTable}}{{AvailableInWorkers}}

متد **`register()`** از رابط {{domxref("PeriodicSyncManager")}} یک درخواست همگام‌سازی دوره‌ای را با برچسب و گزینه‌های مشخص‌شده در مرورگر ثبت می‌کند. این متد یک {{jsxref('Promise')}} برمی‌گرداند که پس از تکمیل ثبت نام، حل می‌شود.

## نحو

```js-nolint
register(tag, options)
```

### پارامترها

- `tag`
  - : یک شناسه {{jsxref('String')}} یکتا.
- `options` {{optional_inline}}
  - : یک {{jsxref('Object')}} شامل داده‌های اختیاری زیر:
    - `minInterval`
      - : حداقل فاصله زمانی (بر حسب میلی‌ثانیه) که همگام‌سازی دوره‌ای باید در آن رخ دهد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} برمی‌گرداند که با {{jsxref('undefined')}} حل می‌شود.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورتی که هیچ {{domxref('ServiceWorker')}} فعالی وجود نداشته باشد، بازگردانده می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : در صورتی که مجوز همگام‌سازی دوره‌ای پس‌زمینه داده نشده باشد، بازگردانده می‌شود.
- `InvalidAccessError` {{domxref("DOMException")}}
  - : در صورتی که پنجره فعال، پنجره اصلی نباشد (از نوع `auxiliary` یا `top-level` نباشد)، بازگردانده می‌شود.

## مثال‌ها

تابع ناهمگام زیر، یک همگام‌سازی دوره‌ای پس‌زمینه را با حداقل فاصله یک روز از یک بافت مرورگر ثبت می‌کند:

```js
async function registerPeriodicNewsCheck() {
  const registration = await navigator.serviceWorker.ready;
  try {
    await registration.periodicSync.register("fetch-news", {
      minInterval: 24 * 60 * 60 * 1000,
    });
  } catch {
    console.log("Periodic Sync could not be registered!");
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [تجربه‌های آفلاین غنی‌تر با API همگام‌سازی دوره‌ای پس‌زمینه](https://developer.chrome.com/docs/capabilities/periodic-background-sync)