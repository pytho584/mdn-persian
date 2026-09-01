---
title: "HTMLMediaElement: durationchange event"
---

---
title: "HTMLMediaElement: durationchange event"
short-title: durationchange
slug: Web/API/HTMLMediaElement/durationchange_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.durationchange_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `durationchange` زمانی به‌وقوع می‌پیوندد که مشخصهٔ `duration` به‌روزرسانی شده باشد.

## دستور زبان

برای استفاده از این رویداد، نام آن را در روش‌هایی مانند `addEventListener()` به کار ببرید، یا یک خاصیت مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("durationchange", (event) => { })

ondurationchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال‌ها یک شنوندهٔ رویداد برای رویداد `durationchange` در HTMLMediaElement اضافه می‌کنند و زمانی که آن مدیریت‌کنندهٔ رویداد به فعال‌شدن رویداد واکنش نشان دهد، یک پیام چاپ می‌کنند.

استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("durationchange", (event) => {
  console.log("Not sure why, but the duration of the video has changed.");
});
```

استفاده از خاصیت مدیریت رویداد `ondurationchange`:

```js
const video = document.querySelector("video");

video.ondurationchange = (event) => {
  console.log("Not sure why, but the duration of the video has changed.");
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
- رویداد {{domxref("HTMLMediaElement.canplay_event", 'canplay')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.canplaythrough_event", 'canplaythrough')}} در HTMLMediaElement
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