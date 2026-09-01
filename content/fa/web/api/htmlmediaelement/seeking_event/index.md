---
title: "HTMLMediaElement: seeking event"
---

---
title: "HTMLMediaElement: seeking event"
short-title: seeking
slug: Web/API/HTMLMediaElement/seeking_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.seeking_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `seeking` زمانی فعال می‌شود که یک عملیات جستجو (seek) آغاز شود، به این معنی که ویژگی بولی `seeking` به `true` تغییر کرده و رسانه در حال جستجوی یک موقعیت جدید است.

این رویداد غیرقابل لغو است و منتشر نمی‌شود (bubble نمی‌کند).

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی event handler تنظیم کنید.

```js-nolint
addEventListener("seeking", (event) => { })

onseeking = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال‌ها یک شنونده رویداد برای رویداد `seeking` عنصر HTMLMediaElement اضافه می‌کنند، سپس هنگامی که آن event handler به فعال شدن رویداد واکنش نشان داد، یک پیام ثبت می‌کنند.

استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("seeking", (event) => {
  console.log("ویدئو در حال جستجوی یک موقعیت جدید است.");
});
```

استفاده از ویژگی event handler `onseeking`:

```js
const video = document.querySelector("video");

video.onseeking = (event) => {
  console.log("ویدئو در حال جستجوی یک موقعیت جدید است.");
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## رویدادهای مرتبط

- رویداد {{domxref("HTMLMediaElement.playing_event", 'playing')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.waiting_event", 'waiting')}} در HTMLMediaElement
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