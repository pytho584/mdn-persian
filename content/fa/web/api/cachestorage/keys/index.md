---
title: "CacheStorage: keys() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CacheStorage/keys"
translated_by: "n8n + AI"
---

---
title: "CacheStorage: keys() method"
short-title: keys()
slug: Web/API/CacheStorage/keys
page-type: web-api-instance-method
browser-compat: api.CacheStorage.keys
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`keys()`** از رابط {{domxref("CacheStorage")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک آرایه شامل رشته‌های متناظر با تمام اشیاء {{domxref("Cache")}} نام‌گذاری شده که توسط شیء {{domxref("CacheStorage")}} ردیابی می‌شوند، به ترتیب ایجادشان، حل می‌شود. از این متد برای پیمایش فهرست تمام اشیاء {{domxref("Cache")}} استفاده کنید.

شما می‌توانید `CacheStorage` را از طریق ویژگی {{domxref("Window.caches")}} در پنجره‌ها یا از طریق ویژگی {{domxref("WorkerGlobalScope.caches")}} در کارگرها دسترسی داشته باشید.

## Syntax

```js-nolint
keys()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک آرایه از نام‌های {{domxref("Cache")}} درون شیء {{domxref("CacheStorage")}} حل می‌شود.

## مثال‌ها

در این قطعه کد، ما منتظر یک رویداد {{domxref("ServiceWorkerGlobalScope.activate_event", "activate")}} می‌مانیم و سپس یک بلوک {{domxref("ExtendableEvent.waitUntil","waitUntil()")}} اجرا می‌کنیم که هر حافظه نهان قدیمی و استفاده‌نشده را قبل از فعال شدن یک سرویس‌ورکر جدید پاک می‌کند. در اینجا یک لیست سفید داریم که شامل نام‌های حافظه‌های نهانی است که می‌خواهیم نگه داریم (`cacheAllowlist`). کلیدهای حافظه‌های نهان را در شیء {{domxref("CacheStorage")}} با استفاده از `keys()` برمی‌گردانیم، سپس هر کلید را بررسی می‌کنیم تا ببینیم آیا در لیست سفید است یا نه. اگر نبود، آن را با استفاده از {{domxref("CacheStorage.delete()")}} حذف می‌کنیم.

```js
this.addEventListener("activate", (event) => {
  const cacheAllowlist = ["v2"];

  event.waitUntil(
    caches.keys().then((keyList) =>
      Promise.all(
        keyList.map((key) => {
          if (!cacheAllowlist.includes(key)) {
            return caches.delete(key);
          }
          return undefined;
        }),
      ),
    ),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از سرویس‌ورکرها](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- {{domxref("Cache")}}
- {{domxref("Window.caches")}} و {{domxref("WorkerGlobalScope.caches")}}