---
title: "Navigator: audioSession property"
short-title: audioSession
slug: Web/API/Navigator/audioSession
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Navigator.audioSession
---

{{APIRef("Audio Session API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`audioSession`** از رابط {{domxref("Navigator")}}، شیء {{domxref("AudioSession")}} مربوط به سند جاری را بازمی‌گرداند.

رابط {{domxref("AudioSession")}} می‌تواند برای کنترل نحوه تعامل صدا از یک برنامه وب با سایر صداهای در حال پخش روی دستگاه استفاده شود. برای مثال، به توسعه‌دهندگان اجازه می‌دهد مشخص کنند که صدای برنامه‌شان باید به تنهایی پخش شود یا همراه با سایر صداهای دستگاه.

## مقدار

یک شیء {{domxref("AudioSession")}}.

## مثال‌ها

### تنظیم نوع نشست صوتی

مثال زیر نوع نشست صوتی را قبل از شروع یک تماس ویدیویی روی `"play-and-record"` تنظیم می‌کند:

```js
navigator.audioSession.type = "play-and-record";

// شروع تماس ویدیویی
const stream = await navigator.mediaDevices.getUserMedia({
  audio: true,
  video: true,
});
localVideo.srcObject = stream;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("AudioSession")}}
- {{domxref("AudioSession.type")}}
- [Audio Session API](/en-US/docs/Web/API/Audio_Session_API)