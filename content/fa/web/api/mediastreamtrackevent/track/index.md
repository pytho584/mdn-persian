---
title: "MediaStreamTrackEvent: track property"
short-title: track
slug: Web/API/MediaStreamTrackEvent/track
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrackEvent.track
---

{{APIRef("Media Capture and Streams")}}

ویژگی فقط‑خواندنی **`track`** از رابط {{domxref("MediaStreamTrackEvent")}}، شیء {{domxref("MediaStreamTrack")}} مرتبط با این رویداد را برمی‌گرداند.

## مقدار

یک شیء {{domxref("MediaStreamTrack")}}.

## مثال‌ها

```js
const stream = new MediaStream();

stream.addEventListener("removetrack", (event) => {
  console.log(`${event.track.kind} track removed`);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای {{domxref("MediaStream/addtrack_event", "addtrack")}} و {{domxref("MediaStream/removetrack_event", "removetrack")}}
- {{domxref("MediaStreamTrack")}}