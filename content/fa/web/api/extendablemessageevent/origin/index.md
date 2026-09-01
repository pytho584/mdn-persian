---
title: "ExtendableMessageEvent: origin property"
short-title: origin
slug: Web/API/ExtendableMessageEvent/origin
page-type: web-api-instance-property
browser-compat: api.ExtendableMessageEvent.origin
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

خاصیت فقط-خواندنی **`origin`** از رابط {{domxref("ExtendableMessageEvent")}}، مبدأ (origin) {{domxref("Client")}}ای را که پیام را فرستاده است برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

زمانی که از کد زیر درون یک service worker برای پاسخ به پیام‌های push با ارسال داده‌های دریافت‌شده از طریق {{domxref("PushMessageData")}} به زمینه‌ی اصلی (main context) از طریق یک [پیام کانال](/en-US/docs/Web/API/Channel_Messaging_API) استفاده شود، شیء رویداد `onmessage` یک `ExtendableMessageEvent` خواهد بود.

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
  console.log(e.origin);
  port = e.ports[0];
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [مثال کد پایه‌ای service workers](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [پیام‌رسانی کانال (Channel Messaging)](/en-US/docs/Web/API/Channel_Messaging_API)