---
title: "MessageEvent: lastEventId property"
short-title: lastEventId
slug: Web/API/MessageEvent/lastEventId
page-type: web-api-instance-property
browser-compat: api.MessageEvent.lastEventId
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`lastEventId`** از رابط {{domxref("MessageEvent")}} یک رشته است که یک شناسه منحصربه‌فرد برای رویداد را نشان می‌دهد.

## مقدار

یک رشته که شناسه را نشان می‌دهد.

## مثال‌ها

```js
myWorker.onmessage = (e) => {
  result.textContent = e.data;
  console.log("Message received from worker");
  console.log(e.lastEventId);
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("ExtendableMessageEvent")}} — مشابه این رابط اما در رابط‌هایی استفاده می‌شود که نیاز به انعطاف‌پذیری بیشتری برای نویسندگان دارند.