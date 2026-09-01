```markdown
---
title: "HTMLMediaElement: volumechange event"
short-title: volumechange
slug: Web/API/HTMLMediaElement/volumechange_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.volumechange_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `volumechange` زمانی فعال می‌شود که ویژگی {{domxref("HTMLMediaElement.volume", "volume")}} یا ویژگی {{domxref("HTMLMediaElement.muted", "muted")}} تغییر کند.

این رویداد قابل لغو نیست و به عناصر بالایی منتشر نمی‌شود.

## نحو (Syntax)

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("volumechange", (event) => { })

onvolumechange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال‌ها یک شنونده رویداد برای رویداد `volumechange` عنصر HTMLMediaElement اضافه می‌کنند و سپس پس از واکنش کنترل‌کننده به فعال شدن رویداد، یک پیام ارسال می‌کنند.

استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("volumechange", (event) => {
  console.log("The volume changed.");
});
```

استفاده از ویژگی کنترل‌کننده رویداد `onvolumechange`:

```js
const video = document.querySelector("video");

video.onvolumechange = (event) => {
  console.log("The volume changed.");
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
- رویداد {{domxref("HTMLMediaElement.loadeddata_event", 'loadeddata')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.canplay_event", 'canplay')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.canplaythrough_event", 'canplaythrough')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.durationchange_event", 'durationchange')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.timeupdate_event", 'timeupdate')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.play_event", 'play')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.pause_event", 'pause')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.ratechange_event", 'ratechange')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.suspend_event", 'suspend')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.emptied_event", 'emptied')}} از HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.stalled_event", 'stalled')}} از HTMLMediaElement

## همچنین ببینید

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}
```