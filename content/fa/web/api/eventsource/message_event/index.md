---
title: "EventSource: message event"
short-title: message
slug: Web/API/EventSource/message_event
page-type: web-api-event
browser-compat: api.EventSource.message_event
---

{{APIRef("Server Sent Events")}}{{AvailableInWorkers}}

رویداد **`message`** از رابط {{domxref("EventSource")}} هنگامی که داده‌ای از طریق یک منبع رویداد دریافت می‌شود، فعال می‌گردد.

این رویداد غیرقابل لغو است و انتشار نمی‌یابد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم نمایید.

```js-nolint
addEventListener("message", (event) => { })

onmessage = (event) => { }
```

## نوع رویداد

یک {{domxref("MessageEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("MessageEvent")}}

## مثال‌ها

در این مثال ساده، یک `EventSource` برای دریافت رویدادها از سرور ایجاد می‌شود؛ صفحه‌ای با نام `sse.php` مسئول تولید رویدادها است.

```js
const evtSource = new EventSource("sse.php");
const eventList = document.querySelector("ul");

evtSource.addEventListener("message", (e) => {
  const newElement = document.createElement("li");

  newElement.textContent = `message: ${e.data}`;
  eventList.appendChild(newElement);
});
```

### معادل onmessage

```js
evtSource.onmessage = (e) => {
  const newElement = document.createElement("li");

  newElement.textContent = `message: ${e.data}`;
  eventList.appendChild(newElement);
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از رویدادهای ارسال‌شده از سمت سرور](/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events)
- [`open`](/en-US/docs/Web/API/EventSource/open_event)
- [`error`](/en-US/docs/Web/API/EventSource/error_event)