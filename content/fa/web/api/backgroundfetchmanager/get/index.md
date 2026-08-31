---
title: "BackgroundFetchManager: get() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchManager/get"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchManager: get() method"
short-title: get()
slug: Web/API/BackgroundFetchManager/get
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BackgroundFetchManager.get
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

متد **`get()`** از رابط {{domxref("BackgroundFetchManager")}} یک {{jsxref("Promise")}} برمی‌گرداند که با {{domxref("BackgroundFetchRegistration")}} مرتبط با `id` ارائه‌شده حل می‌شود، یا اگر `id` پیدا نشد، {{jsxref("undefined")}} برمی‌گرداند.

## نحوۀ استفاده

```js-nolint
get(id)
```

### پارامترها

- `id`
  - : شناسه یک {{domxref("BackgroundFetchRegistration")}} که با فراخوانی {{domxref("BackgroundFetchManager.fetch","fetch()")}} تعریف شده است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک {{domxref("BackgroundFetchRegistration")}} یا {{jsxref("undefined")}} حل می‌شود.

## مثال‌ها

مثال زیر نحوه استفاده از `get()` را برای بازیابی یک {{domxref("BackgroundFetchRegistration")}} نشان می‌دهد. با یک [service worker](/en-US/docs/Web/API/ServiceWorker) فعال، از {{domxref('ServiceWorkerRegistration.backgroundFetch')}} برای دسترسی به شیء `BackgroundFetchManager` و فراخوانی متد `get()` آن استفاده کنید.

```js
navigator.serviceWorker.ready.then(async (swReg) => {
  const bgFetch = await swReg.backgroundFetch.get("my-fetch");
});
// my code block
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}