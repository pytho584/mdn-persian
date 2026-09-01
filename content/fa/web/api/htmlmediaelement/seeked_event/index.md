---
title: "HTMLMediaElement: seeked event"
short-title: seeked
slug: Web/API/HTMLMediaElement/seeked_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.seeked_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `seeked` زمانی به‌کار می‌افتد که عملیات جستجو (seek) به پایان رسیده باشد، موقعیت پخش فعلی تغییر کرده باشد، و ویژگی بولی `seeking` به `false` تغییر یافته باشد.

این رویداد قابل لغو (cancelable) نیست و منتشر (bubble) نمی‌شود.

## Syntax

برای استفاده از نام این رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم یک ویژگی‌کننده رویداد (event handler property) می‌توانید از روش‌های زیر استفاده کنید.

```js-nolint
addEventListener("seeked", (event) => { })

onseeked = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال‌ها یک شنونده رویداد برای رویداد `seeked` در HTMLMediaElement اضافه می‌کنند و سپس هنگامی که آن کنش‌گر رویداد به رویداد فعال‌شده واکنش نشان می‌دهد، یک پیام ارسال می‌کنند.

استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("seeked", (event) => {
  console.log("Video found the playback position it was looking for.");
});
```

استفاده از ویژگی‌کننده رویداد `onseeked`:

```js
const video = document.querySelector("video");

video.onseeked = (event) => {
  console.log("Video found the playback position it was looking for.");
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## رویدادهای مرتبط

- رویداد {{domxref("HTMLMediaElement.playing_event", 'playing')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.waiting_event", 'waiting')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.seeking_event", 'seeking')}} در HTMLMediaElement
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