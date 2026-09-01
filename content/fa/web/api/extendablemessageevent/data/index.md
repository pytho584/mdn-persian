---
title: "ExtendableMessageEvent: data property"
short-title: data
slug: Web/API/ExtendableMessageEvent/data
page-type: web-api-instance-property
browser-compat: api.ExtendableMessageEvent.data
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

ویژگی فقط خواندنی **`data`** در رابط {{domxref("ExtendableMessageEvent")}} داده‌های رویداد را برمی‌گرداند. این ویژگی می‌تواند از هر نوع داده‌ای باشد.

## مقدار

هر نوع داده‌ای.

## مثال‌ها

هنگامی که از کد زیر درون یک سرویس‌ورکر برای پاسخ به پیام‌های پوش با ارسال داده‌های دریافت‌شده از طریق {{domxref("PushMessageData")}} به زمینه‌ی اصلی از طریق یک [پیام کانالی](/en-US/docs/Web/API/Channel_Messaging_API) استفاده می‌شود، شیء رویداد `onmessage` یک `ExtendableMessageEvent` خواهد بود.

```js
let port;

self.addEventListener("push", (e) => {
  const obj = e.data.json();

  if (obj.action === "subscribe" || obj.action === "unsubscribe") {
    port.postMessage(obj);
  } else if (obj.action === "init" || obj.action === "chatMsg") {
    port.postMessage(obj);
  }
});

self.onmessage = (e) => {
  console.log(e.data);
  port = e.ports[0];
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [مثال کد پایه سرویس‌ورکرها](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [پیام‌رسانی کانالی](/en-US/docs/Web/API/Channel_Messaging_API)