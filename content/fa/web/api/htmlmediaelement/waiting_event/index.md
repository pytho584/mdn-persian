---
title: "HTMLMediaElement: waiting event"
short-title: waiting
slug: Web/API/HTMLMediaElement/waiting_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.waiting_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `waiting` زمانی فعال می‌شود که پخش به دلیل کمبود موقت داده متوقف شده باشد.

این رویداد قابل‌لغو (cancelable) نیست و حباب (bubble) نمی‌شود.

## سینتکس

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک خاصیت مدیریت رویداد (event handler) را تنظیم کنید.

```js-nolint
addEventListener("waiting", (event) => { })

onwaiting = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال‌ها یک شنونده رویداد برای رویداد `waiting` در HTMLMediaElement اضافه می‌کنند و سپس وقتی آن مدیریت رویداد به فعال‌شدن رویداد واکنش نشان داد، یک پیام ثبت می‌کنند.

استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("waiting", (event) => {
  console.log("Video is waiting for more data.");
});
```

استفاده از خاصیت مدیریت رویداد `onwaiting`:

```js
const video = document.querySelector("video");

video.onwaiting = (event) => {
  console.log("Video is waiting for more data.");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## رویدادهای مرتبط

- رویداد {{domxref("HTMLMediaElement.playing_event", 'playing')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.seeking_event", 'seeking')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.seeked_event", 'seeked')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.ended_event", 'ended')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.loadedmetadata_event", 'loadedmetadata')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.loadeddata_event", 'loadeddata')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.canplay_event", 'canplay')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.canplaythrough_event", 'canplaythrough')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.durationchange_event", 'durationchange')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.timeupdate_event", 'timeupdate')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.play_event", 'play')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.pause_event", 'pause')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.ratechange_event", 'ratechange')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.volumechange_event", 'volumechange')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.suspend_event", 'suspend')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.emptied_event", 'emptied')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.stalled_event", 'stalled')}} در HTMLMediaElement

## همچنین ببینید

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}