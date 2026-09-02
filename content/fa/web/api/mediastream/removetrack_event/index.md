---
title: "MediaStream: رویداد removetrack"
short-title: removetrack
slug: Web/API/MediaStream/removetrack_event
page-type: web-api-event
browser-compat: api.MediaStream.removetrack_event
---

{{APIRef("Media Capture and Streams")}}

رویداد **`removetrack`** زمانی فعال می‌شود که یک شیء {{domxref("MediaStreamTrack")}} جدید از یک {{domxref("MediaStream")}} حذف شده باشد.

این رویداد قابل لغو نیست و به عناصر بالاتر منتقل نمی‌شود (bubble نمی‌کند).

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}}، یا تنظیم یک ویژگی رویدادگردان (event handler property) می‌توانید به صورت زیر عمل کنید:

```js-nolint
addEventListener("removetrack", (event) => { })

onremovetrack = (event) => { }
```

## نوع رویداد

یک {{domxref("MediaStreamTrackEvent")}} که از {{domxref("Event")}} به ارث برده است.

{{InheritanceDiagram("MediaStreamTrackEvent")}}

## مثال‌ها

استفاده از `addEventListener()`:

```js
const stream = new MediaStream();

stream.addEventListener("removetrack", (event) => {
  console.log(`${event.track.kind} track removed`);
});
```

استفاده از ویژگی رویدادگردان `onremovetrack`:

```js
const stream = new MediaStream();

stream.onremovetrack = (event) => {
  console.log(`${event.track.kind} track removed`);
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رویداد مرتبط: [`addtrack`](/en-US/docs/Web/API/MediaStream/addtrack_event)
- این رویداد در اهداف [`AudioTrackList`](/en-US/docs/Web/API/AudioTrackList): [`removetrack`](/en-US/docs/Web/API/AudioTrackList/removetrack_event)
- این رویداد در اهداف [`VideoTrackList`](/en-US/docs/Web/API/VideoTrackList): [`removetrack`](/en-US/docs/Web/API/VideoTrackList/removetrack_event)
- [API Media Capture and Streams](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [WebRTC](/en-US/docs/Web/API/WebRTC_API)