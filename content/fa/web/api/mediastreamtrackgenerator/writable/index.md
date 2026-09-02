---
title: "MediaStreamTrackGenerator: writable property"
short-title: writable
slug: Web/API/MediaStreamTrackGenerator/writable
page-type: web-api-instance-property
status:
  - experimental
  - non-standard
browser-compat: api.MediaStreamTrackGenerator.writable
---

{{APIRef("Insertable Streams for MediaStreamTrack API")}}{{SeeCompatTable}}{{Non-standard_Header}}

ویژگی **`writable`** در رابط {{domxref("MediaStreamTrackGenerator")}} یک {{domxref("WritableStream")}} برمی‌گرداند. این امکان را فراهم می‌کند که فریم‌های رسانه‌ای به `MediaStreamTrackGenerator` نوشته شوند. این فریم‌ها می‌توانند صوتی یا تصویری باشند. نوع آن‌ها بر اساس نوع `MediaStreamTrackGenerator` که ایجاد شده تعیین می‌شود.

## مقدار

یک {{domxref("WritableStream")}}.

## مثال‌ها

در مثال زیر، فریم‌های ویدیو تبدیل شده و سپس به {{domxref("WritableStream")}} که از طریق `MediaStreamTrackGenerator.writable` در دسترس است نوشته می‌شوند.

```js
const trackProcessor = new MediaStreamTrackProcessor({ track: videoTrack });
const trackGenerator = new MediaStreamTrackGenerator({ kind: "video" });

/* */

trackProcessor.readable
  .pipeThrough(transformer)
  .pipeTo(trackGenerator.writable);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}