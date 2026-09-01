---
title: "EventSource: error event"
short-title: error
slug: Web/API/EventSource/error_event
page-type: web-api-event
browser-compat: api.EventSource.error_event
---

{{APIRef("Server Sent Events")}}{{AvailableInWorkers}}

رویداد **`error`** در رابط برنامه‌نویسی {{domxref("EventSource")}} زمانی رخ می‌دهد که اتصال به یک منبع رویداد (event source) با شکست مواجه شده و باز نشود.

این رویداد غیرقابل‌لغو است و به سمت بالا منتشر نمی‌شود (bubble نمی‌کند).

## Syntax

برای استفاده از این رویداد، نام آن را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به‌کار ببرید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) را تنظیم کنید.

```js-nolint
addEventListener("error", (event) => { })

onerror = (event) => { }
```

## Event type

یک {{domxref("Event")}} عمومی.

## Examples

```js
const evtSource = new EventSource("sse.php");

// addEventListener version
evtSource.addEventListener("error", (e) => {
  console.log("An error occurred while attempting to connect.");
});

// onerror version
evtSource.onerror = (e) => {
  console.log("An error occurred while attempting to connect.");
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using server-sent events](/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events)
- [`open`](/en-US/docs/Web/API/EventSource/open_event)
- [`message`](/en-US/docs/Web/API/EventSource/message_event)
