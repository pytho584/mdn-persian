---
title: "HTMLMediaElement: encrypted event"
short-title: encrypted
slug: Web/API/HTMLMediaElement/encrypted_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.encrypted_event
---

{{APIRef("Encrypted Media Extensions")}}

رویداد `encrypted` زمانی فعال می‌شود که داده‌های اولیه‌سازی در رسانه یافت شود که نشان می‌دهد رسانه رمزنگاری شده است.

این رویداد قابل لغو کردن نیست و منتشر نمی‌شود (bubble نمی‌شود).

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی handler رویداد تنظیم کنید.

```js-nolint
addEventListener("encrypted", (event) => { })

onencrypted = (event) => { }
```

## نوع رویداد

یک {{domxref("MediaEncryptedEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("MediaEncryptedEvent")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}
- {{domxref("MediaEncryptedEvent")}}