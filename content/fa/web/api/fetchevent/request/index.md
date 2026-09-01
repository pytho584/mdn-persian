---
title: "FetchEvent: request property"
short-title: request
slug: Web/API/FetchEvent/request
page-type: web-api-instance-property
browser-compat: api.FetchEvent.request
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنی **`request`** در رابط {{domxref("FetchEvent")}}، شیء {{domxref("Request")}}ای را که رویداد handler را فعال کرده است، برمی‌گرداند.

این ویژگی غیرقابل‌نمایش (non-nullable) است (از نسخه ۴۶ به بعد در فایرفاکس). اگر درخواستی از طریق روش دیگری ارائه نشود، شیء `options` سازنده باید شامل یک درخواست باشد (به {{domxref("FetchEvent.FetchEvent", "FetchEvent()")}} مراجعه کنید).

## مقدار

یک شیء {{domxref("Request")}}.

## مثال‌ها

این قطعه کد از [نمونهٔ service worker fetch](https://github.com/GoogleChrome/samples/blob/gh-pages/service-worker/prefetch/service-worker.js) گرفته شده است ([اجرای زندهٔ نمونهٔ fetch](https://googlechrome.github.io/samples/service-worker/prefetch/)). رویدادگردان {{domxref("ServiceWorkerGlobalScope.fetch_event", "onfetch")}} به رویداد `fetch` گوش می‌دهد. وقتی این رویداد رخ دهد، یک Promise به صفحهٔ کنترل‌شده بازگردانده می‌شود که به {{domxref("FetchEvent.respondWith", "FetchEvent.respondWith()")}} ارسال می‌شود. این Promise به اولین پاسخِ تطبیق‌یافته با URL درخواست در شیء {{domxref("Cache")}} منتهی می‌شود. اگر هیچ تطبیقی یافت نشود، کد پاسخ را از شبکه دریافت می‌کند.

کد همچنین استثناهایی را که از عملیات {{domxref("Window/fetch", "fetch()")}} پرتاب می‌شوند مدیریت می‌کند. توجه داشته باشید که پاسخ خطای HTTP (مثلاً 404) باعث ایجاد استثنا نمی‌شود؛ بلکه یک شیء پاسخ عادی با کد خطای مناسب برمی‌گرداند.

```js
self.addEventListener("fetch", (event) => {
  console.log("Handling fetch event for", event.request.url);

  event.respondWith(
    caches.match(event.request).then((response) => {
      if (response) {
        console.log("Found response in cache:", response);

        return response;
      }
      console.log("No response found in cache. About to fetch from network…");

      return fetch(event.request)
        .then((response) => {
          console.log("Response from network is:", response);

          return response;
        })
        .catch((error) => {
          console.error("Fetching failed:", error);

          throw error;
        });
    }),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [مثال کد پایهٔ Service workers](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [استفاده از Web Workers](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers)