---
title: "HTMLMediaElement: emptied event"
short-title: emptied
slug: Web/API/HTMLMediaElement/emptied_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.emptied_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `emptied` زمانی رخ می‌دهد که رسانه خالی شده باشد؛ به عنوان مثال، این رویداد زمانی ارسال می‌شود که رسانه قبلاً بارگذاری شده (یا به طور جزئی بارگذاری شده) باشد و متد `load()` برای بارگذاری مجدد آن فراخوانی شود.

این رویداد قابل لغو نیست و در درخت DOM منتشر نمی‌شود (bubble نمی‌کند).

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} قرار دهید، یا از ویژگی مدیریت رویداد (event handler property) استفاده کنید.

```js-nolint
addEventListener("emptied", (event) => { })

onemptied = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال‌ها یک شنونده رویداد برای رویداد `emptied` عنصر HTMLMediaElement اضافه می‌کنند و سپس وقتی آن مدیریت رویداد به رخ دادن رویداد واکنش نشان داد، یک پیام ارسال می‌کنند.

استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("emptied", (event) => {
  console.log("اه اوه. رسانه خالی است. آیا load() را صدا زده‌اید؟");
});
```

استفاده از ویژگی مدیریت رویداد `onemptied`:

```js
const video = document.querySelector("video");

video.onemptied = (event) => {
  console.log("اه اوه. رسانه خالی است. آیا load() را صدا زده‌اید؟");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## رویدادهای مرتبط

- رویداد {{domxref("HTMLMediaElement.playing_event", 'playing')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.waiting_event", 'waiting')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.seeking_event", 'seeking')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.seeked_event", 'seeked')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.ended_event", 'ended')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.loadedmetadata_event", 'loadedmetadata')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.loadeddata_event", 'loadeddata')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.canplay_event", 'canplay')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.canplaythrough_event", 'canplaythrough')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.durationchange_event", 'durationchange')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.timeupdate_event", 'timeupdate')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.play_event", 'play')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.pause_event", 'pause')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.ratechange_event", 'ratechange')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.volumechange_event", 'volumechange')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.suspend_event", 'suspend')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.stalled_event", 'stalled')}} عنصر HTMLMediaElement

## همچنین ببینید

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}