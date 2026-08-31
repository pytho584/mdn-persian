---
title: "AudioWorkletNode: processorerror event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletNode/processorerror_event"
translated_by: "n8n + AI"
---

---
title: "AudioWorkletNode: processorerror event"
short-title: processorerror
slug: Web/API/AudioWorkletNode/processorerror_event
page-type: web-api-event
browser-compat: api.AudioWorkletNode.processorerror_event
---

{{ APIRef("Web Audio API") }}{{SecureContext_Header}}

رویداد `processorerror` زمانی آتش می‌شود که {{domxref("AudioWorkletProcessor")}} پشت گره در سازنده‌اش، متد {{domxref("AudioWorkletProcessor.process", "process")}}، یا هر متد کلاس تعریف‌شده توسط کاربر استثنا پرتاب کند.

پس از پرتاب یک استثنا، پردازنده (و در نتیجه گره) در طول عمر خود خروجی سکوت خواهد داشت.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("processorerror", (event) => { })

onprocessorerror = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

برای اطلاع از زمانی که پردازنده استثنا پرتاب می‌کند، می‌توانید یک کنترل‌کننده به نمونه {{domxref("AudioWorkletNode")}} خود با استفاده از {{domxref("EventTarget.addEventListener", "addEventListener()")}} اضافه کنید، مانند این:

```js
whiteNoiseNode.addEventListener("processorerror", (event) => {
  console.error("There was an error!");
});
```

متناوباً، می‌توانید از ویژگی کنترل‌کننده رویداد `onprocessorerror` برای برقراری یک کنترل‌کننده برای رویداد `processorerror` استفاده کنید:

```js
whiteNoiseNode.onprocessorerror = (event) => {
  console.error("There was an error!");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)