---
title: "CacheStorage: delete() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CacheStorage/delete"
translated_by: "n8n + AI"
short-title: delete()
slug: Web/API/CacheStorage/delete
page-type: web-api-instance-method
browser-compat: api.CacheStorage.delete
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`delete()`** از رابط {{domxref("CacheStorage")}}، شیء {{domxref("Cache")}} منطبق با `cacheName` را پیدا می‌کند و در صورت یافتن، آن شیء {{domxref("Cache")}} را حذف کرده و یک {{jsxref("Promise")}} برمی‌گرداند که به `true` resolve می‌شود. اگر هیچ شیء {{domxref("Cache")}} یافت نشود، به `false` resolve می‌شود.

می‌توانید به `CacheStorage` از طریق ویژگی {{domxref("Window.caches")}} در پنجره‌ها یا از طریق ویژگی {{domxref("WorkerGlobalScope.caches")}} در کارگران دسترسی پیدا کنید.

## Syntax

```js-nolint
delete(cacheName)
```

### Parameters

- `cacheName`
  - : نام حافظه نهانی که می‌خواهید حذف کنید.

### Return value

یک {{jsxref("Promise")}} که اگر شیء {{domxref("Cache")}} پیدا و حذف شود به `true` و در غیر این صورت به `false` resolve می‌شود.

## Examples

در این قطعه کد، ما منتظر یک رویداد activate می‌مانیم و سپس یک بلوک {{domxref("ExtendableEvent.waitUntil","waitUntil()")}} اجرا می‌کنیم که حافظه‌های نهان قدیمی و استفاده نشده را قبل از فعال شدن یک سرویس‌ورکر جدید پاک می‌کند. در اینجا یک آرایه از نام‌های حافظه نهان که می‌خواهیم نگه داریم (`cachesToKeep`) داریم. کلیدهای حافظه‌های نهان را در شیء {{domxref("CacheStorage")}} با استفاده از {{domxref("CacheStorage.keys")}} برمی‌گردانیم، سپس هر کلید را بررسی می‌کنیم که آیا در آرایه است یا خیر. اگر نباشد، آن را با استفاده از `delete()` حذف می‌کنیم.

```js
this.addEventListener("activate", (event) => {
  const cachesToKeep = ["v2"];

  event.waitUntil(
    caches.keys().then((keyList) =>
      Promise.all(
        keyList.map((key) => {
          if (!cachesToKeep.includes(key)) {
            return caches.delete(key);
          }
          return undefined;
        }),
      ),
    ),
  );
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- {{domxref("Cache")}}
- {{domxref("Window.caches")}} and {{domxref("WorkerGlobalScope.caches")}}