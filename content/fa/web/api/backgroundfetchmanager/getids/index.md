---
title: "BackgroundFetchManager: getIds() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchManager/getIds"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchManager: getIds() method"
short-title: getIds()
slug: Web/API/BackgroundFetchManager/getIds
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BackgroundFetchManager.getIds
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

متد **`getIds()`** از رابط {{domxref("BackgroundFetchManager")}} شناسه‌های تمام واکشی‌های پس‌زمینه ثبت‌شده را برمی‌گرداند.

## نحو

```js-nolint
getIds()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک {{jsxref('Array')}} از {{jsxref('String', 'رشته‌ها')}} حل می‌شود.

### استثناها

هیچ‌کدام.

## مثال‌ها

مثال زیر نحوه بازیابی شناسه‌های تمام واکشی‌های پس‌زمینه ثبت‌شده را نشان می‌دهد. با یک [service worker](/en-US/docs/Web/API/ServiceWorker) فعال، از ویژگی {{domxref('ServiceWorkerRegistration.backgroundFetch')}} برای دسترسی به شیء `BackgroundFetchManager` استفاده کنید و متد `getIds()` آن را فراخوانی کنید.

```js
navigator.serviceWorker.ready.then(async (swReg) => {
  const ids = await swReg.backgroundFetch.getIds();
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}