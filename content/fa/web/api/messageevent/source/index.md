---
title: "MessageEvent: source property"
short-title: source
slug: Web/API/MessageEvent/source
page-type: web-api-instance-property
browser-compat: api.MessageEvent.source
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

خاصیت فقط-خواندنی **`source`** از رابط {{domxref("MessageEvent")}} یک `MessageEventSource` است (که می‌تواند یک شیء {{glossary("WindowProxy")}}، {{domxref("MessagePort")}} یا {{domxref("ServiceWorker")}} باشد) و فرستنده پیام را نشان می‌دهد.

## مقدار

یک `MessageEventSource` (که می‌تواند یک شیء {{glossary("WindowProxy")}}، {{domxref("MessagePort")}} یا {{domxref("ServiceWorker")}} باشد) که فرستنده پیام را نشان می‌دهد.

## مثال‌ها

```js
myWorker.onmessage = (e) => {
  result.textContent = e.data;
  console.log("Message received from worker");
  console.log(e.source);
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ExtendableMessageEvent")}} — مشابه این رابط است اما در رابط‌هایی استفاده می‌شود که نیاز به انعطاف‌پذیری بیشتری برای نویسندگان دارند.