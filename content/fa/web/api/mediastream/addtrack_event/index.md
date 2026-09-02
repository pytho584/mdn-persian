---
title: "MediaStream: addtrack event"
short-title: addtrack
slug: Web/API/MediaStream/addtrack_event
page-type: web-api-event
browser-compat: api.MediaStream.addtrack_event
---

{{APIRef("Media Capture and Streams")}}

رویداد **`addtrack`** زمانی فعال می‌شود که یک شیء [`MediaStreamTrack`](/en-US/docs/Web/API/MediaStreamTrack) جدید به یک [`MediaStream`](/en-US/docs/Web/API/MediaStream) اضافه شده باشد.

این رویداد قابل لغو نیست و در درخت DOM منتشر نمی‌شود (bubble نمی‌کند).

## نحو (Syntax)

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی handler رویداد تنظیم کنید.

```js-nolint
addEventListener("addtrack", (event) => { })

onaddtrack = (event) => { }
```

## نوع رویداد

یک {{domxref("MediaStreamTrackEvent")}} که از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("MediaStreamTrackEvent")}}

## مثال‌ها

استفاده از `addEventListener()`:

```js
const stream = new MediaStream();

stream.addEventListener("addtrack", (event) => {
  console.log(`یک track جدید از نوع ${event.track.kind} اضافه شد`);
});
```

استفاده از ویژگی handler رویداد `onaddtrack`:

```js
const stream = new MediaStream();

stream.onaddtrack = (event) => {
  console.log(`یک track جدید از نوع ${event.track.kind} اضافه شد`);
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رویداد مرتبط: [`removetrack`](/en-US/docs/Web/API/MediaStream/removetrack_event)
- این رویداد در اهداف [`AudioTrackList`](/en-US/docs/Web/API/AudioTrackList): [`addtrack`](/en-US/docs/Web/API/AudioTrackList/addtrack_event)
- این رویداد در اهداف [`VideoTrackList`](/en-US/docs/Web/API/VideoTrackList): [`addtrack`](/en-US/docs/Web/API/VideoTrackList/addtrack_event)
- [API Media Capture and Streams](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [WebRTC](/en-US/docs/Web/API/WebRTC_API)