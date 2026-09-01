---
title: "ExtendableMessageEvent: source property"
short-title: source
slug: Web/API/ExtendableMessageEvent/source
page-type: web-api-instance-property
browser-compat: api.ExtendableMessageEvent.source
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

ویژگی فقط خواندنی **`source`** در رابط {{domxref("ExtendableMessageEvent")}} یک ارجاع به شیء {{domxref("Client")}} که پیام از آن ارسال شده است را بازمی‌گرداند.

## مقدار

یک شیء {{domxref("Client")}}، {{domxref("ServiceWorker")}} یا {{domxref("MessagePort")}}.

## مثال‌ها

زمانی که کد زیر درون یک سرویس‌ورکر برای پاسخ به پیام‌های فشاری با ارسال داده‌های دریافت‌شده از طریق {{domxref("PushMessageData")}} به زمینه اصلی از طریق یک [پیام کانال](/en-US/docs/Web/API/Channel_Messaging_API) استفاده می‌شود، شیء رویداد `onmessage` یک `ExtendableMessageEvent` خواهد بود.

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
  console.log(e.source);
  port = e.ports[0];
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [مثال کد پایه سرویس‌ورکرها](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [پیام‌رسانی کانال](/en-US/docs/Web/API/Channel_Messaging_API)