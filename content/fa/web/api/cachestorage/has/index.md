---
title: "CacheStorage: has() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CacheStorage/has"
translated_by: "n8n + AI"
---

---
title: "CacheStorage: has() method"
short-title: has()
slug: Web/API/CacheStorage/has
page-type: web-api-instance-method
browser-compat: api.CacheStorage.has
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`has()`** از رابط {{domxref("CacheStorage")}} یک {{jsxref("Promise")}} را برمی‌گرداند که اگر یک شیء {{domxref("Cache")}} با `cacheName` مطابقت داشته باشد، به `true` resolve می‌شود.

شما می‌توانید از طریق ویژگی {{domxref("Window.caches")}} در پنجره‌ها یا از طریق ویژگی {{domxref("WorkerGlobalScope.caches")}} در کارگرها به `CacheStorage` دسترسی داشته باشید.

## سینتکس

```js-nolint
has(cacheName)
```

### پارامترها

- `cacheName`
  - : رشته‌ای است که نام شیء {{domxref("Cache")}} مورد جستجو را در {{domxref("CacheStorage")}} نشان می‌دهد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که اگر حافظه پنهان وجود داشته باشد به `true` و اگر وجود نداشته باشد به `false` resolve می‌شود.

## مثال‌ها

مثال زیر ابتدا بررسی می‌کند که آیا حافظه پنهانی به نام `'v1'` وجود دارد. اگر وجود داشته باشد، فهرستی از دارایی‌ها را به آن اضافه می‌کنیم. اگر وجود نداشته باشد، یک تابع راه‌اندازی حافظه پنهان را اجرا می‌کنیم.

```js
caches
  .has("v1")
  .then((hasCache) => {
    if (!hasCache) {
      someCacheSetupFunction();
    } else {
      caches.open("v1").then((cache) => cache.addAll(myAssets));
    }
  })
  .catch(() => {
    // Handle exception here.
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- {{domxref("Cache")}}
- {{domxref("Window.caches")}} و {{domxref("WorkerGlobalScope.caches")}}