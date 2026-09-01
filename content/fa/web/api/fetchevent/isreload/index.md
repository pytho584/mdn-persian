---
title: "FetchEvent: isReload property"
short-title: isReload
slug: Web/API/FetchEvent/isReload
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.FetchEvent.isReload
---

{{APIRef("Service Workers API")}}{{deprecated_header}}{{Non-standard_header}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنی **`isReload`** در رابط {{domxref("FetchEvent")}} اگر رویداد توسط تلاش کاربر برای بارگذاری مجدد صفحه ایجاد شده باشد، مقدار `true` و در غیر این صورت `false` برمی‌گرداند. فشردن دکمهٔ بازنشانی (refresh) یک بارگذاری مجدد محسوب می‌شود، در حالی که کلیک روی یک پیوند یا فشردن دکمهٔ بازگشت چنین نیست.

## مقدار

یک مقدار بولین.

## مثال‌ها

```js
self.addEventListener("fetch", (event) => {
  event.respondWith(async () => {
    if (event.isReload) {
      // Return something
    } else {
      // Return something else
    }
  })();
});
```

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [مثال کد پایهٔ Service workers](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [استفاده از web workers](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers)