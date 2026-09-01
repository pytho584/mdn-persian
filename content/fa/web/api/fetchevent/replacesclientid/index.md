---
title: "FetchEvent: replacesClientId property"
short-title: replacesClientId
slug: Web/API/FetchEvent/replacesClientId
page-type: web-api-instance-property
browser-compat: api.FetchEvent.replacesClientId
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنی **`replacesClientId`** در رابط {{domxref("FetchEvent")}}، شامل {{domxref("Client.id", "id")}} آن {{domxref("Client", "client")}}ی است که هنگام پیمایش صفحه (navigation) جایگزین می‌شود.

برای مثال، هنگام پیمایش از صفحه A به صفحه B، `replacesClientId` شناسهٔ کلاینتی است که با صفحه A مرتبط است. اگر از `about:blank` به صفحه دیگری پیمایش کنید، این مقدار می‌تواند یک رشتهٔ خالی باشد؛ زیرا کلاینت مربوط به `about:blank` دوباره استفاده می‌شود، نه اینکه جایگزین گردد.

علاوه بر این، اگر درخواست fetch یک پیمایش نباشد، `replacesClientId` یک رشتهٔ خالی خواهد بود. از این ویژگی می‌توان برای دسترسی/ارتباط با کلاینتی استفاده کرد که درست قبل از پیمایش، به‌زودی جایگزین خواهد شد.

## مقدار

یک رشته (string).

## مثال‌ها

```js
self.addEventListener("fetch", (event) => {
  console.log(event.replacesClientId);
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