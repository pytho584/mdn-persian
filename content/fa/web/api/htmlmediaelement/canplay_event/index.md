---
title: "HTMLMediaElement: canplay event"
short-title: canplay
slug: Web/API/HTMLMediaElement/canplay_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.canplay_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `canplay` زمانی رخ می‌دهد که عامل کاربر بتواند رسانه را پخش کند، اما تخمین بزند که داده‌های کافی برای پخش رسانه تا انتها بدون نیاز به توقف برای بافر کردن محتوای بیشتر بارگذاری نشده است.

این رویداد قابل لغو نیست و به عناصر والد حباب نمی‌شود.

## نحو

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید یا یک ویژگی مدیریت‌کننده رویداد (event handler) تنظیم کنید.

```js-nolint
addEventListener("canplay", (event) => { })

oncanplay = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال‌ها یک شنونده رویداد به رویداد `canplay` در HTMLMediaElement اضافه می‌کنند و پس از واکنش مدیریت‌کننده رویداد به اجرای رویداد، یک پیام در کنسول ثبت می‌کنند.

با استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("canplay", (event) => {
  console.log("Video can start, but not sure it will play through.");
});
```

با استفاده از ویژگی مدیریت‌کننده رویداد `oncanplay`:

```js
const video = document.querySelector("video");

video.oncanplay = (event) => {
  console.log("Video can start, but not sure it will play through.");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## رویدادهای مرتبط

- رویداد {{domxref("HTMLMediaElement.playing_event", 'playing')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.waiting_event", 'waiting')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.seeking_event", 'seeking')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.seeked_event", 'seeked')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.ended_event", 'ended')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.loadedmetadata_event", 'loadedmetadata')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.loadeddata_event", 'loadeddata')}} در HTMLMediaElement
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

## جستارهای وابسته

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}