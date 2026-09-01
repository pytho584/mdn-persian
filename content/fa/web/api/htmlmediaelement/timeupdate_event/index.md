---
title: "HTMLMediaElement: رویداد timeupdate"
short-title: timeupdate
slug: Web/API/HTMLMediaElement/timeupdate_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.timeupdate_event
---

{{APIRef("HTMLMediaElement")}}

رویداد `timeupdate` زمانی شلیک می‌شود که زمان مشخص‌شده توسط ویژگی `currentTime` به‌روزرسانی شده باشد.

فرکانس این رویداد به بار سیستم بستگی دارد، اما تقریباً بین ۴ هرتز تا ۶۶ هرتز پرتاب می‌شود (به شرطی که اجرای event handlerها بیش از ۲۵۰ میلی‌ثانیه طول نکشد). به عامل‌های کاربری توصیه می‌شود که فرکانس رویداد را بر اساس بار سیستم و هزینه متوسط پردازش رویداد در هر بار تغییر دهند، به طوری که به‌روزرسانی‌های رابط کاربری بیش از آنچه عامل کاربری در حین رمزگشایی ویدیو به راحتی می‌تواند مدیریت کند، نباشد.

این رویداد قابل لغو (cancelable) نیست و منتشر (bubble) نمی‌شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی event handler تنظیم کنید.

```js-nolint
addEventListener("timeupdate", (event) => { })

ontimeupdate = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال‌ها یک شنونده رویداد برای رویداد `timeupdate` HTMLMediaElement اضافه می‌کنند و سپس هنگامی که آن event handler به شلیک رویداد واکنش نشان داد، یک پیام ارسال می‌کنند. به یاد داشته باشید که فرکانس رویداد به بار سیستم بستگی دارد.

استفاده از `addEventListener()`:

```js
const video = document.querySelector("video");

video.addEventListener("timeupdate", (event) => {
  console.log("ویژگی currentTime به‌روزرسانی شده است. دوباره.");
});
```

استفاده از ویژگی event handler `ontimeupdate`:

```js
const video = document.querySelector("video");

video.ontimeupdate = (event) => {
  console.log("ویژگی currentTime به‌روزرسانی شده است. دوباره.");
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
- رویداد {{domxref("HTMLMediaElement.loadedmetadata_event", 'loadedmetadata')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.loadeddata_event", 'loadeddata')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.canplay_event", 'canplay')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.canplaythrough_event", 'canplaythrough')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.durationchange_event", 'durationchange')}} در HTMLMediaElement
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