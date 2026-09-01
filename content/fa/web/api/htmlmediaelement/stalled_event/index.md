---
title: "HTMLMediaElement: stalled event"
---

---
title: "HTMLMediaElement: stalled event"
short-title: stalled
slug: Web/API/HTMLMediaElement/stalled_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.stalled_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `stalled` زمانی رخ می‌دهد که عامل کاربر (user agent) در حال تلاش برای دریافت داده‌های رسانه‌ای است، اما داده‌ها به‌طور غیرمنتظره در دسترس قرار نمی‌گیرند.

این رویداد قابل لغو نیست و حباب نمی‌زند.

## سینتکس

از نام این رویداد در روش‌هایی مانند `addEventListener()` استفاده کنید، یا یک ویژگیِ کنترل‌کنندهٔ رویداد را تنظیم کنید.

```js-nolint
addEventListener("stalled", (event) => { })

onstalled = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال‌ها یک شنوندهٔ رویداد برای رویداد `stalled` عنصر HTMLMediaElement اضافه می‌کنند و سپس وقتی آن کنترل‌کنندهٔ رویداد به فعال‌شدن رویداد واکنش نشان داد، پیامی را چاپ می‌کنند.

با استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("stalled", (event) => {
  console.log("Failed to fetch data, but trying.");
});
```

با استفاده از ویژگی کنترل‌کنندهٔ رویداد `onstalled`:

```js
const video = document.querySelector("video");

video.onstalled = (event) => {
  console.log("Failed to fetch data, but trying.");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

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
- رویداد {{domxref("HTMLMediaElement.durationchange_event", 'durationchange')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.timeupdate_event", 'timeupdate')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.play_event", 'play')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.pause_event", 'pause')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.ratechange_event", 'ratechange')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.volumechange_event", 'volumechange')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.suspend_event", 'suspend')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.emptied_event", 'emptied')}} در HTMLMediaElement

## همچنین ببینید

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}