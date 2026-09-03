---
title: "NavigationPreloadManager: enable() method"
short-title: enable()
slug: Web/API/NavigationPreloadManager/enable
page-type: web-api-instance-method
browser-compat: api.NavigationPreloadManager.enable
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`enable()`** در رابط {{domxref("NavigationPreloadManager")}} برای فعال‌سازی بارگذاری پیش‌دستی (preload) منابعی که توسط سرویس‌ورکر مدیریت می‌شوند استفاده می‌شود.
این متد یک وعده (Promise) برمی‌گرداند که با `undefined` حل می‌شود.

این متد باید در هندلر رویداد `activate` سرویس‌ورکر فراخوانی شود تا اطمینان حاصل شود که قبل از هر هندلر رویداد `fetch` اجرا می‌شود.

## نحو (Syntax)

```js-nolint
enable()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{jsxref('undefined')}} حل می‌شود.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : هیچ کارگر فعالی با ثبت‌نام (registration) که این {{domxref("NavigationPreloadManager")}} به آن تعلق دارد مرتبط نیست.

## مثال‌ها

کد زیر نحوه فعال‌سازی بارگذاری پیش‌دستی را نشان می‌دهد، ابتدا با استفاده از {{domxref("ServiceWorkerRegistration.navigationPreload")}} بررسی می‌کند که آیا این قابلیت پشتیبانی می‌شود یا خیر.

```js
addEventListener("activate", (event) => {
  event.waitUntil(
    (async () => {
      if (self.registration.navigationPreload) {
        // Enable navigation preloads!
        await self.registration.navigationPreload.enable();
      }
    })(),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("NavigationPreloadManager.disable()")}}