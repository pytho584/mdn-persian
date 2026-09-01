---
title: "HTMLMediaElement: pause event"
short-title: pause
slug: Web/API/HTMLMediaElement/pause_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.pause_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `pause` زمانی ارسال می‌شود که درخواست توقف یک فعالیت پردازش شده و فعالیت وارد حالت توقف شده است. این حالت معمولاً پس از آن رخ می‌دهد که رسانه از طریق فراخوانی متد {{domxref("HTMLMediaElement.pause", "pause()")}} عنصر متوقف شده باشد.

این رویداد پس از بازگشت متد `pause()` و تغییر ویژگی {{domxref("HTMLMediaElement.paused", "paused")}} عنصر رسانه به `true` ارسال می‌شود.

این رویداد قابل ابطال نیست و به سمت بالا حباب نمی‌شود.

## سینتکس

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("pause", (event) => { })

onpause = (event) => { }
```

## نوع رویداد

یک رویداد عمومی از نوع {{domxref("Event")}}.

## مثال‌ها

این مثال‌ها یک شنونده رویداد برای رویداد `pause` عنصر HTMLMediaElement اضافه می‌کنند و هنگامی که مدیریت‌کننده رویداد به فعال‌شدن رویداد واکنش نشان می‌دهد، یک پیام می‌نویسند.

استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("pause", (event) => {
  console.log(
    "The Boolean paused property is now 'true'. Either the pause() method was called or the autoplay attribute was toggled.",
  );
});
```

استفاده از ویژگی مدیریت رویداد `onpause`:

```js
const video = document.querySelector("video");

video.onpause = (event) => {
  console.log(
    "The Boolean paused property is now 'true'. Either the pause() method was called or the autoplay attribute was toggled.",
  );
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
- {{domxref("SpeechSynthesisUtterance")}}