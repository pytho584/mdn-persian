---
title: "EventSource: url property"
short-title: url
slug: Web/API/EventSource/url
page-type: web-api-instance-property
browser-compat: api.EventSource.url
---

{{APIRef("Server Sent Events")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`url`** از رابط {{domxref("EventSource")}} یک رشته را برمی‌گرداند که نشانی URL منبع را نشان می‌دهد.

## مقدار

رشته‌ای که نشانی URL منبع را نشان می‌دهد.

## مثال‌ها

```js
const evtSource = new EventSource("sse.php");
console.log(evtSource.url);
```

> [!NOTE]
> می‌توانید یک مثال کامل را در گیت‌هاب ببینید — [Simple SSE demo using PHP](https://github.com/mdn/dom-examples/tree/main/server-sent-events).

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("EventSource")}}