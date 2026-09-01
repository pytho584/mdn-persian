---
title: "DedicatedWorkerGlobalScope: messageerror event"
short-title: messageerror
slug: Web/API/DedicatedWorkerGlobalScope/messageerror_event
page-type: web-api-event
browser-compat: api.DedicatedWorkerGlobalScope.messageerror_event
---

{{APIRef("Web Workers API")}}{{AvailableInWorkers("dedicated")}}

رویداد `messageerror` روی یک شیء {{domxref('DedicatedWorkerGlobalScope')}} زمانی به‌وقوع می‌پیوندد که پیامی دریافت کند که امکان تبدیل (deserialize) آن وجود نداشته باشد.

این رویداد قابل لغو (cancellable) نیست و به سمت بالا حباب (bubble) نمی‌شود.

## دستور زبان

نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا به‌عنوان یک ویژگی کنترل‌کننده رویداد استفاده کنید.

```js-nolint
addEventListener("messageerror", (event) => { })

onmessageerror = (event) => { }
```

## نوع رویداد

یک {{domxref("MessageEvent")}}. از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("MessageEvent")}}

## مثال‌ها

گوش دادن به رویداد `messageerror` با استفاده از [`addEventListener()`](/en-US/docs/Web/API/EventTarget/addEventListener):

```js
// worker.js

self.addEventListener("messageerror", (event) => {
  self.postMessage("Error receiving message");
  console.error(event);
});
```

به همین ترتیب، اما با استفاده از ویژگی کنترل‌کننده رویداد `onmessageerror`:

```js
// worker.js

self.onmessageerror = (event) => {
  self.postMessage("Error receiving message");
  console.error(event);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DedicatedWorkerGlobalScope")}}
- {{domxref("WorkerGlobalScope")}}
- رویدادهای مرتبط: [`message`](/en-US/docs/Web/API/DedicatedWorkerGlobalScope/message_event)
- [`Worker.postMessage()`](/en-US/docs/Web/API/Worker/postMessage)
- [استفاده از پیام‌رسانی کانالی](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)