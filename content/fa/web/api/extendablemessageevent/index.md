---
title: "ExtendableMessageEvent"
slug: Web/API/ExtendableMessageEvent
page-type: web-api-interface
browser-compat: api.ExtendableMessageEvent
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

رابط **`ExtendableMessageEvent`** از [API Service Worker](/en-US/docs/Web/API/Service_Worker_API) نشان‌دهندهٔ شیء رویداد یک رویداد {{domxref("ServiceWorkerGlobalScope/message_event", "message")}} است که روی یک سرویس‌ورکر (وقتی پیامی روی {{domxref("ServiceWorkerGlobalScope")}} از زمینه‌ای دیگر دریافت می‌شود) فعال می‌شود — طول عمر چنین رویدادهایی را افزایش می‌دهد.

این رابط از رابط {{domxref("ExtendableEvent")}} ارث‌بری می‌کند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("ExtendableMessageEvent.ExtendableMessageEvent","ExtendableMessageEvent()")}}
  - : یک نمونهٔ جدید از شیء `ExtendableMessageEvent` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود {{domxref("ExtendableEvent")}} به ارث می‌برد._

- {{domxref("ExtendableMessageEvent.data")}} {{ReadOnlyInline}}
  - : داده‌های رویداد را برمی‌گرداند. می‌تواند از هر نوع داده‌ای باشد. اگر در رویداد `messageerror` ارسال شود، این ویژگی `null` خواهد بود.
- {{domxref("ExtendableMessageEvent.origin")}} {{ReadOnlyInline}}
  - : origin (مبدأ) {{domxref("Client")}}ای را که پیام را فرستاده برمی‌گرداند.
- {{domxref("ExtendableMessageEvent.lastEventId")}} {{ReadOnlyInline}}
  - : در [رویدادهای ارسال‌شده از سرور (server-sent events)](/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events)، آخرین شناسهٔ رویداد منبع رویداد را نشان می‌دهد.
- {{domxref("ExtendableMessageEvent.source")}} {{ReadOnlyInline}}
  - : یک ارجاع به شیء {{domxref("Client")}}ای که پیام را فرستاده برمی‌گرداند.
- {{domxref("ExtendableMessageEvent.ports")}} {{ReadOnlyInline}}
  - : آرایه‌ای حاوی اشیاء {{domxref("MessagePort")}} که درگاه‌های کانال پیام مرتبط را نشان می‌دهند برمی‌گرداند.

## روش‌های نمونه

_روش‌ها را از والد خود {{domxref("ExtendableEvent")}} به ارث می‌برد._

## مثال‌ها

در مثال زیر، یک صفحه از طریق {{domxref("ServiceWorkerRegistration.active")}} یک دستگیره (handle) به شیء {{domxref("ServiceWorker")}} می‌گیرد و سپس تابع `postMessage()` آن را فراخوانی می‌کند.

```js
// در صفحه‌ای که تحت کنترل است
if (navigator.serviceWorker) {
  navigator.serviceWorker.register("service-worker.js");

  navigator.serviceWorker.addEventListener("message", (event) => {
    // event یک شیء MessageEvent است
    console.log(`سرویس‌ورکر برای من پیامی فرستاد: ${event.data}`);
  });

  navigator.serviceWorker.ready.then((registration) => {
    registration.active.postMessage("سلام سرویس‌ورکر");
  });
}
```

سرویس‌ورکر می‌تواند با گوش دادن به رویداد `message` پیام را دریافت کند:

```js
// در سرویس‌ورکر
addEventListener("message", (event) => {
  // event یک شیء ExtendableMessageEvent است
  console.log(`کارخواه برای من پیامی فرستاد: ${event.data}`);

  event.source.postMessage("سلام کارخواه");
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [مثال کد ابتدایی Service Workers](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [Channel Messaging](/en-US/docs/Web/API/Channel_Messaging_API)