---
title: "MessageEvent: data property"
short-title: data
slug: Web/API/MessageEvent/data
page-type: web-api-instance-property
browser-compat: api.MessageEvent.data
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`data`** در رابط {{domxref("MessageEvent")}} داده‌ای را نشان می‌دهد که فرستندهٔ پیام ارسال کرده است.

## مقدار

داده ارسال‌شده توسط فرستندهٔ پیام؛ این داده می‌تواند از هر نوع data ای باشد، بسته به چیزی که این رویداد را به وجود آورده است.

## مثال‌ها

```js
myWorker.onmessage = (e) => {
  result.textContent = e.data;
  console.log("Message received from worker");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ExtendableMessageEvent")}} — مشابه همین رابط است، اما در رابط‌هایی استفاده می‌شود که نیاز به انعطاف‌پذیری بیشتری برای توسعه‌دهندگان دارند.