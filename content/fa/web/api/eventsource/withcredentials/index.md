---
title: "EventSource: withCredentials property"
short-title: withCredentials
slug: Web/API/EventSource/withCredentials
page-type: web-api-instance-property
browser-compat: api.EventSource.withCredentials
---

{{APIRef("Server Sent Events")}}{{AvailableInWorkers}}

خصوصیت فقط‌خواندنی **`withCredentials`** در رابط {{domxref("EventSource")}} یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا شیء `EventSource` با اعتبارنامه‌های CORS مقداردهی شده است یا خیر.

## مقدار

یک مقدار بولی که نشان می‌دهد آیا شیء `EventSource` با اعتبارنامه‌های CORS ایجاد شده است (`true`) یا خیر (`false`، پیش‌فرض).

## مثال‌ها

```js
const evtSource = new EventSource("sse.php");
console.log(evtSource.withCredentials);
```

> [!NOTE]
> می‌توانید یک مثال کامل را در GitHub بیابید — به [نمونه ساده SSE با استفاده از PHP](https://github.com/mdn/dom-examples/tree/main/server-sent-events) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("EventSource")}}