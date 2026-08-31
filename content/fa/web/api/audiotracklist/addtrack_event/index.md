---
title: "AudioTrackList: addtrack event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioTrackList/addtrack_event"
translated_by: "n8n + AI"
---

---
title: "AudioTrackList: addtrack event"
short-title: addtrack
slug: Web/API/AudioTrackList/addtrack_event
page-type: web-api-event
browser-compat: api.AudioTrackList.addtrack_event
---

{{APIRef("HTML DOM")}}

رویداد `addtrack` زمانی فعال می‌شود که یک ترک به [`AudioTrackList`](/en-US/docs/Web/API/AudioTrackList) اضافه شود.

## نحو

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("addtrack", (event) => { })

onaddtrack = (event) => { }
```

## نوع رویداد

یک {{domxref("TrackEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("TrackEvent")}}

## توضیحات

### محرک

رویداد `addtrack` هرگاه یک ترک جدید به عنصر رسانه‌ای که ترک‌های صوتی آن توسط شیء `AudioTrackList` نمایش داده می‌شوند، اضافه شود، فراخوانی می‌شود. این اتفاق زمانی می‌افتد که ترک‌ها هنگام اولین اتصال رسانه به عنصر اضافه می‌شوند؛ برای هر ترک صوتی در منبع رسانه یک رویداد `addtrack` رخ می‌دهد.

این رویداد قابل لغو نیست و منتشر نمی‌شود.

### موارد استفاده

می‌توانید از این رویداد برای واکنش به در دسترس شدن یک ترک صوتی جدید استفاده کنید. برای مثال، ممکن است بخواهید عناصر رابط کاربری خود را به‌روزرسانی کنید تا انتخاب کاربر از ترک صوتی جدید امکان‌پذیر شود.

## مثال‌ها

استفاده از `addEventListener()`:

```js
const videoElement = document.querySelector("video");

videoElement.audioTracks.addEventListener("addtrack", (event) => {
  console.log(`Audio track: ${event.track.label} added`);
});
```

استفاده از ویژگی مدیریت رویداد `onaddtrack`:

```js
const videoElement = document.querySelector("video");

videoElement.audioTracks.onaddtrack = (event) => {
  console.log(`Audio track: ${event.track.label} added`);
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط: [`removetrack`](/en-US/docs/Web/API/AudioTrackList/removetrack_event)، [`change`](/en-US/docs/Web/API/AudioTrackList/change_event)
- این رویداد بر روی [`VideoTrackList`](/en-US/docs/Web/API/VideoTrackList) هدف: [`addtrack`](/en-US/docs/Web/API/VideoTrackList/addtrack_event)
- این رویداد بر روی [`MediaStream`](/en-US/docs/Web/API/MediaStream) هدف: [`addtrack`](/en-US/docs/Web/API/MediaStream/addtrack_event)
- [API ضبط و جریان‌های رسانه](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [WebRTC](/en-US/docs/Web/API/WebRTC_API)