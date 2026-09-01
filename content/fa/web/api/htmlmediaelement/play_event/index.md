---
title: "HTMLMediaElement: play event"
short-title: play
slug: Web/API/HTMLMediaElement/play_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.play_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `play` زمانی فعال میشود که خاصیت `paused` از `true` به `false` تغییر کند؛ این تغییر میتواند در نتیجهٔ فراخوانی متد `play` یا به دلیل ویژگی `autoplay` رخ دهد.

این رویداد قابل لغو (cancelable) نیست و در درخت DOM منتشر (bubble) نمیشود.

## نحو (Syntax)

برای مدیریت این رویداد میتوانید نام رویداد را در روشهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید یا از ویژگیِ handler رویداد استفاده کنید.

```js-nolint
addEventListener("play", (event) => { })

onplay = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثالها

در این مثالها، یک شنوندهٔ رویداد برای رویداد `play` عنصر HTMLMediaElement اضافه شده و سپس وقتی آن شنونده به فعال شدن رویداد واکنش نشان دهد، یک پیام ثبت میشود.

استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("play", (event) => {
  console.log(
    "The Boolean paused property is now 'false'. Either the play() method was called or the autoplay attribute was toggled.",
  );
});
```

استفاده از ویژگیِ handler رویداد `onplay`:

```js
const video = document.querySelector("video");

video.onplay = (event) => {
  console.log(
    "The Boolean paused property is now 'false'. Either the play() method was called or the autoplay attribute was toggled.",
  );
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

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
- رویداد {{domxref("HTMLMediaElement.pause_event", 'pause')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.ratechange_event", 'ratechange')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.volumechange_event", 'volumechange')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.suspend_event", 'suspend')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.emptied_event", 'emptied')}} عنصر HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.stalled_event", 'stalled')}} عنصر HTMLMediaElement

## همچنین ببینید

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}