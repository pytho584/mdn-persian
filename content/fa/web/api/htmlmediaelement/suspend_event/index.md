---
title: "HTMLMediaElement: suspend event"
short-title: suspend
slug: Web/API/HTMLMediaElement/suspend_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.suspend_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `suspend` زمانی رخ می‌دهد که عامل کاربر (user agent) عمداً داده‌های رسانه را واکشی نمی‌کند. در این حالت، {{domxref("HTMLMediaElement.networkState")}} به `HTMLMediaElement.NETWORK_IDLE` تنظیم می‌شود. این اتفاق می‌تواند زمانی رخ دهد که داده‌ای برای بارگیری وجود نداشته باشد، یا بارگیری غیرضروری باشد؛ برای مثال، مرورگر ممکن است تصمیم بگیرد فقط ۵ دقیقه از یک ویدیو را از پیش بافر کند، که در این صورت بارگیری تا زمانی که کاربر بخش بیشتری از ویدیو را تماشا کند، متوقف می‌شود.

این رویداد غیرقابل لغو است و منتشر نمی‌شود.

## Syntax

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی (property) برای کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("suspend", (event) => { })

onsuspend = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال‌ها یک شنونده رویداد برای رویداد `suspend` در HTMLMediaElement اضافه می‌کنند و سپس هنگامی که کنترل‌کننده رویداد به وقوع رویداد واکنش نشان می‌دهد، پیامی ارسال می‌کنند.

استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("suspend", (event) => {
  console.log("Data loading has been suspended.");
});
```

استفاده از ویژگی کنترل‌کننده رویداد `onsuspend`:

```js
const video = document.querySelector("video");

video.onsuspend = (event) => {
  console.log("Data loading has been suspended.");
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## رویدادهای مرتبط

- The HTMLMediaElement {{domxref("HTMLMediaElement.playing_event", 'playing')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.waiting_event", 'waiting')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.seeking_event", 'seeking')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.seeked_event", 'seeked')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.ended_event", 'ended')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.loadedmetadata_event", 'loadedmetadata')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.loadeddata_event", 'loadeddata')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.canplay_event", 'canplay')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.canplaythrough_event", 'canplaythrough')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.durationchange_event", 'durationchange')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.timeupdate_event", 'timeupdate')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.play_event", 'play')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.pause_event", 'pause')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.ratechange_event", 'ratechange')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.volumechange_event", 'volumechange')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.emptied_event", 'emptied')}} event
- The HTMLMediaElement {{domxref("HTMLMediaElement.stalled_event", 'stalled')}} event

## همچنین ببینید

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)