---
title: "FetchEvent: clientId property"
short-title: clientId
slug: Web/API/FetchEvent/clientId
page-type: web-api-instance-property
browser-compat: api.FetchEvent.clientId
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنی **`clientId`** در رابط {{domxref("FetchEvent")}}، شناسهٔ {{domxref("Client")}}ای را برمی‌گرداند که سرویس‌ورکر فعلی آن را کنترل می‌کند.

سپس می‌توان این شناسه را به متد {{domxref("Clients.get()")}} داد تا کلاینت مرتبط بازیابی شود.

## مقدار

یک رشته که نمایندهٔ شناسهٔ کلاینت است.

## مثال‌ها

```js
self.addEventListener("fetch", (event) => {
  console.log(event.clientId);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [نمونه کد پایه سرویس‌ورکرها](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [استفاده از web workers](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers)