---
title: "HTMLMediaElement: loadedmetadata event"
short-title: loadedmetadata
slug: Web/API/HTMLMediaElement/loadedmetadata_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.loadedmetadata_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `loadedmetadata` زمانی صادر می‌شود که فراداده بارگذاری شده باشد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کنندهٔ رویداد تنظیم کنید.

```js-nolint
addEventListener("loadedmetadata", (event) => { })

onloadedmetadata = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال‌ها یک شنوندهٔ رویداد برای رویداد `loadedmetadata` در HTMLMediaElement اضافه می‌کنند و سپس، وقتی آن کنترل‌کننده به بروز رویداد واکنش نشان داد، پیامی را چاپ می‌کنند.

استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("loadedmetadata", (event) => {
  console.log(
    "The duration and dimensions of the media and tracks are now known.",
  );
});
```

استفاده از ویژگی کنترل‌کنندهٔ رویداد `onloadedmetadata`:

```js
const video = document.querySelector("video");

video.onloadedmetadata = (event) => {
  console.log(
    "The duration and dimensions of the media and tracks are now known.",
  );
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

## جستارهای وابسته

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}