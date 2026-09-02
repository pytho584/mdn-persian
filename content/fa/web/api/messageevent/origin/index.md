---
title: "MessageEvent: origin property"
short-title: origin
slug: Web/API/MessageEvent/origin
page-type: web-api-instance-property
browser-compat: api.MessageEvent.origin
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`origin`** در رابط {{domxref("MessageEvent")}} یک رشته است که مبدأ فرستندهٔ پیام را نشان می‌دهد.

## مقدار

رشته‌ای که مبدأ را نشان می‌دهد.

## مثال‌ها

```js
myWorker.onmessage = (e) => {
  result.textContent = e.data;
  console.log("Message received from worker");
  console.log(e.origin);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ExtendableMessageEvent")}} — مشابه این رابط است، اما در رابط‌هایی استفاده می‌شود که نیاز به انعطاف بیشتری برای نویسندگان دارند.