---
title: "ExtendableMessageEvent: ports property"
short-title: ports
slug: Web/API/ExtendableMessageEvent/ports
page-type: web-api-instance-property
browser-compat: api.ExtendableMessageEvent.ports
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

خاصیت فقط‌خواندنی **`ports`** در رابط {{domxref("ExtendableMessageEvent")}} آرایه‌ای از اشیاء {{domxref("MessagePort")}} را برمی‌گرداند که نمایانگر پورت‌های کانال پیام مرتبط هستند (کانالی که پیام از طریق آن ارسال می‌شود).

## مقدار

آرایه‌ای از اشیاء {{domxref("MessagePort")}}.

## مثال‌ها

هنگامی که کد زیر درون یک service worker برای پاسخ به پیام‌های push با ارسال داده‌های دریافت‌شده از طریق {{domxref("PushMessageData")}} به زمینه اصلی (main context) از طریق یک [پیام کانال](/en-US/docs/Web/API/Channel_Messaging_API) استفاده می‌شود، شیء رویداد `onmessage` یک `ExtendableMessageEvent` خواهد بود.

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
  port = e.ports[0];
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [مثال کد پایه service workers](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [پیام‌رسانی کانال (Channel Messaging)](/en-US/docs/Web/API/Channel_Messaging_API)