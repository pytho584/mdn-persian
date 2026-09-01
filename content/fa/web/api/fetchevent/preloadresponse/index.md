---
title: "FetchEvent: preloadResponse property"
short-title: preloadResponse
slug: Web/API/FetchEvent/preloadResponse
page-type: web-api-instance-property
browser-compat: api.FetchEvent.preloadResponse
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنی **`preloadResponse`** از رابط {{domxref("FetchEvent")}} یک {{jsxref("Promise")}} برمی‌گرداند که اگر [پیش‌بارگذاری ناوبری](/en-US/docs/Web/API/NavigationPreloadManager) فعال شده باشد، به {{domxref("Response")}} مربوط به آن resolve می‌شود؛ در غیر این صورت به `undefined` resolve می‌شود.

پیش‌بارگذاری ناوبری زمانی انجام می‌شود که [پیش‌بارگذاری ناوبری فعال باشد](/en-US/docs/Web/API/NavigationPreloadManager/enable)، درخواست از نوع `GET` باشد، و درخواست، یک درخواست ناوبری باشد (درخواستی که مرورگر هنگام بارگذاری صفحه‌ها و iframeها ایجاد می‌کند).

یک service worker می‌تواند در کنترل‌کننده‌ی رویداد fetch خود منتظر این promise بماند تا تکمیل یک درخواست fetch را که در هنگام راه‌اندازی service worker انجام شده است پیگیری کند.

## مقدار

یک {{jsxref("Promise")}} که به یک {{domxref("Response")}} یا در غیر این صورت به `undefined` resolve می‌شود.

## مثال

این قطعه کد از مقاله‌ی «[سرعت‌بخشی به Service Worker با پیش‌بارگذاری ناوبری](https://web.dev/blog/navigation-preload)» گرفته شده است.

کنترل‌کننده‌ی رویداد {{domxref("ServiceWorkerGlobalScope.fetch_event", "onfetch")}} به رویداد `fetch` گوش می‌دهد. وقتی این رویداد فعال شود، کنترل‌کننده {{domxref("FetchEvent.respondWith", "FetchEvent.respondWith()")}} را فراخوانی می‌کند تا یک promise را به صفحه‌ی تحت‌کنترل بازگرداند. این promise با منبع درخواست‌شده resolve خواهد شد.

اگر یک درخواست URL منطبق در شیء {{domxref("Cache")}} وجود داشته باشد، کد یک promise برای دریافت پاسخ از حافظه‌ی نهان (cache) برمی‌گرداند. اگر مورد منطبقی در حافظه‌ی نهان یافت نشود، کد promise موجود در `preloadResponse` را برمی‌گرداند. اگر نه پاسخِ منطبق در حافظه‌ی نهان وجود داشته باشد و نه پاسخِ پیش‌بارگذاری‌شده، کد پاسخ را از شبکه دریافت و promise مرتبط را برمی‌گرداند.

```js
addEventListener("fetch", (event) => {
  event.respondWith(
    (async () => {
      const preloadResponsePromise = event.preloadResponse;

      // Respond from the cache if we can
      const cachedResponse = await caches.match(event.request);
      if (cachedResponse) {
        // Keep the navigation preload request alive even if we do not use its response.
        event.waitUntil(preloadResponsePromise.catch(() => undefined));
        return cachedResponse;
      }

      // Else, use the preloaded response, if it's there
      const response = await preloadResponsePromise;
      if (response) return response;

      // Else try the network.
      return fetch(event.request);
    })(),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [سرعت‌بخشی به Service Worker با پیش‌بارگذاری ناوبری](https://web.dev/blog/navigation-preload)
- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [مثال کد پایه‌ی Service Workers](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [استفاده از Web Workers](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers)