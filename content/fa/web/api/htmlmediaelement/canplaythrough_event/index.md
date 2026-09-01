---
title: "HTMLMediaElement: canplaythrough event"
short-title: canplaythrough
slug: Web/API/HTMLMediaElement/canplaythrough_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.canplaythrough_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `canplaythrough` زمانی رخ می‌دهد که عامل کاربر بتواند رسانه را پخش کند و تخمین بزند که داده کافی برای پخش رسانه تا انتهای آن بارگیری شده است، بدون اینکه نیاز به توقف برای بافر کردن بیشتر محتوا باشد.

این رویداد لغوپذیر نیست و حباب نمی‌شود.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("canplaythrough", (event) => { })

oncanplaythrough = (event) => { }
```

## Event type

یک رویداد عمومی از نوع {{domxref("Event")}}.

## Examples

این مثال‌ها یک شنونده رویداد برای رویداد `canplaythrough` عنصر HTMLMediaElement اضافه می‌کنند و سپس هنگامی که آن مدیریت رویداد به رخ دادن رویداد واکنش نشان می‌دهد، یک پیام را ثبت می‌کنند.

استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("canplaythrough", (event) => {
  console.log(
    "I think I can play through the entire video without having to stop to buffer.",
  );
});
```

استفاده از ویژگی مدیریت رویداد `oncanplaythrough`:

```js
const video = document.querySelector("video");

video.oncanplaythrough = (event) => {
  console.log(
    "I think I can play through the entire video without having to stop to buffer.",
  );
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## Related Events

- رویداد {{domxref("HTMLMediaElement.playing_event", 'playing')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.waiting_event", 'waiting')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.seeking_event", 'seeking')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.seeked_event", 'seeked')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.ended_event", 'ended')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.loadedmetadata_event", 'loadedmetadata')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.loadeddata_event", 'loadeddata')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.canplay_event", 'canplay')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.durationchange_event", 'durationchange')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.timeupdate_event", 'timeupdate')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.play_event", 'play')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.pause_event", 'pause')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.ratechange_event", 'ratechange')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.volumechange_event", 'volumechange')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.suspend_event", 'suspend')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.emptied_event", 'emptied')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.stalled_event", 'stalled')}} در HTMLMediaElement

## See also

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}