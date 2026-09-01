---
title: "ExtendableMessageEvent: lastEventId property"
short-title: lastEventId
slug: Web/API/ExtendableMessageEvent/lastEventId
page-type: web-api-instance-property
browser-compat: api.ExtendableMessageEvent.lastEventId
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنی **`lastEventID`** در رابط {{domxref("ExtendableMessageEvent")}}، در [رویدادهای ارسال‌شده توسط سرور](/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events)، آخرین شناسه رویداد منبع رویداد را نشان می‌دهد. این مقدار یک رشته خالی است.

## مقدار

یک رشته.

## مثال‌ها

وقتی کد زیر درون یک service worker برای پاسخ به پیام‌های فشاری (push) استفاده می‌شود و داده‌های دریافتی از طریق {{domxref("PushMessageData")}} را با استفاده از [پیام‌رسانی کانالی](/en-US/docs/Web/API/Channel_Messaging_API) به زمینه اصلی ارسال می‌کند، شیء رویدادِ `onmessage` یک `ExtendableMessageEvent` خواهد بود.

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
  console.log(e.lastEventId);
  port = e.ports[0];
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [مثال کد پایه service workerها](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [پیام‌رسانی کانالی](/en-US/docs/Web/API/Channel_Messaging_API)