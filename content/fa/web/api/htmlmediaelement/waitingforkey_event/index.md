---
title: "HTMLMediaElement: waitingforkey event"
short-title: waitingforkey
slug: Web/API/HTMLMediaElement/waitingforkey_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.waitingforkey_event
---

{{APIRef("Encrypted Media Extensions")}}

رویداد `waitingforkey` زمانی برای یک عنصر رسانه‌ای رخ می‌دهد که آن عنصر برای نخستین بار نتواند پخش را ادامه دهد، زیرا برای رمزگشایی داده‌های بعدی به کلید نیاز است و پخش متوقف شده است.

اگر فریم ویدیو و/یا داده‌های صوتی مربوط به موقعیت فعلی پخش رمزگشایی شده باشند، {{domxref("HTMLMediaElement.readyState", "readyState")}} روی [`HAVE_CURRENT_DATA`](/en-US/docs/Web/API/HTMLMediaElement/readyState#htmlmediaelement.have_current_data) تنظیم می‌شود. در غیر این صورت، از جمله اگر داده‌ها قبلاً در دسترس بوده‌اند اما دیگر در دسترس نیستند، `readyState` روی [`HAVE_METADATA`](/en-US/docs/Web/API/HTMLMediaElement/readyState#htmlmediaelement.have_metadata) تنظیم می‌شود.

## سینتکس

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("waitingforkey", (event) => { })

onwaitingforkey = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}