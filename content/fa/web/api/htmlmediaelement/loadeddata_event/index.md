---
title: "HTMLMediaElement: loadeddata event"
short-title: loadeddata
slug: Web/API/HTMLMediaElement/loadeddata_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.loadeddata_event
---

{{APIRef("HTMLMediaElement")}}

رویداد **`loadeddata`** زمانی رخ می‌دهد که فریم مربوط به موقعیت پخش جاری رسانه بارگیری کامل شده باشد؛ معمولاً اولین فریم.

> [!NOTE]
> این رویداد در دستگاه‌های همراه/تبلت در صورتی که گزینه ذخیره‌سازی داده در تنظیمات مرورگر فعال باشد، رخ نخواهد داد.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم نمایید.

```js-nolint
addEventListener("loadeddata", (event) => { })

onloadeddata = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال‌ها یک شنونده رویداد برای رویداد `loadeddata` عنصر HTMLMediaElement اضافه می‌کنند و سپس هنگامی که کنترل‌کننده رویداد به وقوع رویداد واکنش نشان داد، یک پیام ارسال می‌کنند.

استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("loadeddata", (event) => {
  console.log(
    "Yay! The readyState just increased to  " +
      "HAVE_CURRENT_DATA or greater for the first time.",
  );
});
```

استفاده از ویژگی کنترل‌کننده رویداد `onloadeddata`:

```js
const video = document.querySelector("video");

video.onloadeddata = (event) => {
  console.log(
    "Yay! The readyState just increased to  " +
      "HAVE_CURRENT_DATA or greater for the first time.",
  );
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## رویدادهای مرتبط

- رویداد {{domxref("HTMLMediaElement.playing_event", 'playing')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.waiting_event", 'waiting')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.seeking_event", 'seeking')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.seeked_event", 'seeked')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.ended_event", 'ended')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.loadedmetadata_event", 'loadedmetadata')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.canplay_event", 'canplay')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.canplaythrough_event", 'canplaythrough')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.durationchange_event", 'durationchange')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.timeupdate_event", 'timeupdate')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.play_event", 'play')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.pause_event", 'pause')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.ratechange_event", 'ratechange')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.volumechange_event", 'volumechange')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.suspend_event", 'suspend')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.emptied_event", 'emptied')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.stalled_event", 'stalled')}} از HTMLMediaElement

## همچنین ببینید

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}