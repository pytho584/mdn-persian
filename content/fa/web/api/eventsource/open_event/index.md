---
title: "EventSource: open event"
short-title: open
slug: Web/API/EventSource/open_event
page-type: web-api-event
browser-compat: api.EventSource.open_event
---

{{APIRef("Server Sent Events")}}{{AvailableInWorkers}}

رویداد **`open`** در رابط {{domxref("EventSource")}} زمانی که یک اتصال با یک منبع رویداد باز می‌شود، فعال می‌گردد.

این رویداد قابل لغو نیست و منتشر نمی‌شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("open", (event) => { })

onopen = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

```js
const evtSource = new EventSource("sse.php");

// addEventListener version
evtSource.addEventListener("open", (e) => {
  console.log("The connection has been established.");
});

// onopen version
evtSource.onopen = (e) => {
  console.log("The connection has been established.");
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از رویدادهای ارسال‌شده توسط سرور](/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events)
- {{domxref("EventSource/error_event", "error")}}
- {{domxref("EventSource/message_event", "message")}}