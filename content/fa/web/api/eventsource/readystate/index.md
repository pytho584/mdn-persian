---
title: "EventSource: readyState property"
short-title: readyState
slug: Web/API/EventSource/readyState
page-type: web-api-instance-property
browser-compat: api.EventSource.readyState
---

{{APIRef("Server Sent Events")}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`readyState`** از رابط {{domxref("EventSource")}} عددی را برمی‌گرداند که وضعیت اتصال را نشان می‌دهد.

## مقدار

عددی که یکی از سه ثابت وضعیت ممکن تعریف‌شده در رابط {{domxref("EventSource")}} است:

- `EventSource.CONNECTING` (0)
  - : اتصال هنوز باز نشده است.
- `EventSource.OPEN` (1)
  - : اتصال باز است و آمادهٔ ارتباط.
- `EventSource.CLOSED` (2)
  - : اتصال بسته است یا نمی‌تواند باز شود.

## مثال‌ها

```js
const evtSource = new EventSource("sse.php");
console.log(evtSource.readyState);
```

> [!NOTE]
> می‌توانید یک مثال کامل را در GitHub پیدا کنید — به [دموی ساده SSE با استفاده از PHP](https://github.com/mdn/dom-examples/tree/main/server-sent-events) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("EventSource")}}