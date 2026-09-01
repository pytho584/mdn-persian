---
title: "HTMLMediaElement: ended event"
short-title: ended
slug: Web/API/HTMLMediaElement/ended_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.ended_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `ended` زمانی رخ می‌دهد که پخش یا جریان (streaming) به دلیل رسیدن به انتهای رسانه یا در دسترس نبودن داده‌ی بیشتر متوقف شود.

این رویداد بر اساس {{domxref("HTMLMediaElement")}} ({{HTMLElement("audio")}} و {{HTMLElement("video")}}) هنگامی رخ می‌دهد که پخش به انتهای رسانه می‌رسد.

این رویداد قابل لغو (cancelable) نیست و رویداد حباب‌دار (bubbling) نیز نیست.

> [!NOTE]
> رویداد `ended` هنگامی رخ نمی‌دهد که ویژگی [`loop`](/en-US/docs/Web/API/HTMLMediaElement/loop) برابر `true` باشد و [`playbackRate`](/en-US/docs/Web/API/HTMLMediaElement/playbackRate) غیرمنفی باشد.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} وارد کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("ended", (event) => { })

onended = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال‌ها یک شنونده رویداد برای رویداد `ended` عنصر HTMLMediaElement اضافه می‌کنند و سپس زمانی که آن کنترل‌کننده به رخ دادن رویداد واکنش نشان داد، یک پیام ثبت می‌کنند.

استفاده با `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("ended", (event) => {
  console.log(
    "Video stopped either because it has finished playing or no further data is available.",
  );
});
```

استفاده با ویژگی کنترل‌کننده رویداد `onended`:

```js
const video = document.querySelector("video");

video.onended = (event) => {
  console.log(
    "Video stopped either because it has finished playing or no further data is available.",
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
- [Media Capture and Streams](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
  - رویداد `ended` در [`MediaStreamTrack`](/en-US/docs/Web/API/MediaStreamTrack/ended_event)

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
  - [رویداد ended در Web audio API](/en-US/docs/Web/API/AudioScheduledSourceNode/ended_event)