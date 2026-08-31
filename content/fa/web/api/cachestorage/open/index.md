---
title: "CacheStorage: open() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CacheStorage/open"
translated_by: "n8n + AI"
---

---
title: "CacheStorage: open() method"
short-title: open()
slug: Web/API/CacheStorage/open
page-type: web-api-instance-method
browser-compat: api.CacheStorage.open
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`open()`** از رابط {{domxref("CacheStorage")}} یک {{jsxref("Promise")}} را برمی‌گرداند که به شیء {{domxref("Cache")}} مطابق با `cacheName` حل می‌شود.

می‌توانید از طریق ویژگی {{domxref("Window.caches")}} در پنجره‌ها یا از طریق ویژگی {{domxref("WorkerGlobalScope.caches")}} در کارگران به `CacheStorage` دسترسی پیدا کنید.

> [!NOTE]
> اگر {{domxref("Cache")}} مشخص شده وجود نداشته باشد، یک حافظه نهان جدید با آن `cacheName` ایجاد می‌شود و یک {{jsxref("Promise")}} که به این شیء {{domxref("Cache")}} جدید حل می‌شود، بازگردانده می‌شود.

## نحو (Syntax)

```js-nolint
open(cacheName)
```

### پارامترها

- `cacheName`
  - : نام حافظه نهانی که می‌خواهید باز کنید.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به شیء {{domxref("Cache")}} درخواست شده حل می‌شود.

## مثال‌ها

این مثال از [نمونه سرویس‌ورکر ساده](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker) MDN گرفته شده است (نمونه [سرویس‌ورکر ساده در حال اجرا](https://bncb2v.csb.app/) را ببینید). در اینجا منتظر می‌مانیم تا یک {{domxref("InstallEvent")}} رخ دهد، سپس {{domxref("ExtendableEvent.waitUntil","waitUntil()")}} را اجرا می‌کنیم تا فرآیند نصب برنامه را مدیریت کند. این کار شامل فراخوانی `CacheStorage.open()` برای ایجاد یک حافظه نهان جدید و سپس استفاده از {{domxref("Cache.addAll()")}} برای افزودن مجموعه‌ای از دارایی‌ها به آن است.

```js
self.addEventListener("install", (event) => {
  event.waitUntil(
    caches
      .open("v1")
      .then((cache) =>
        cache.addAll([
          "/",
          "/index.html",
          "/style.css",
          "/app.js",
          "/image-list.js",
          "/star-wars-logo.jpg",
          "/gallery/bountyHunters.jpg",
          "/gallery/myLittleVader.jpg",
          "/gallery/snowTroopers.jpg",
        ]),
      ),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- {{domxref("Cache")}}
- {{domxref("Window.caches")}} و {{domxref("WorkerGlobalScope.caches")}}