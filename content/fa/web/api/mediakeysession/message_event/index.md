---
title: "MediaKeySession: message event"
short-title: message
slug: Web/API/MediaKeySession/message_event
page-type: web-api-event
browser-compat: api.MediaKeySession.message_event
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

رویداد **`message`** از رابط {{domxref("MediaKeySession")}} زمانی رخ می‌دهد که یک پیام توسط ماژول رمزگشایی محتوا تولید می‌شود.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کنندهٔ رویداد تنظیم کنید.

```js-nolint
addEventListener("message", (event) => { })

onmessage = (event) => { }
```

## نوع رویداد

این رویداد از نوع {{domxref("MediaKeyMessageEvent")}} است و از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("MediaKeyMessageEvent")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}