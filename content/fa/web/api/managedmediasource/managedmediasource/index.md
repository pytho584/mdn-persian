---
title: "ManagedMediaSource: ManagedMediaSource() constructor"
short-title: ManagedMediaSource()
slug: Web/API/ManagedMediaSource/ManagedMediaSource
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.ManagedMediaSource.ManagedMediaSource
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}{{SeeCompatTable}}

سازندهٔ **`ManagedMediaSource()`** از رابط {{domxref("ManagedMediaSource")}} یک نمونهٔ جدید از شیء `ManagedMediaSource` را می‌سازد و برمی‌گرداند که هیچ بافر منبعی به آن مرتبط نیست.

## نحو

```js-nolint
new ManagedMediaSource()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک نمونهٔ جدید از شیء {{domxref("ManagedMediaSource")}}.

## مثال‌ها

### ایجاد یک ManagedMediaSource و متصل کردن آن به یک عنصر ویدئو

مثال زیر یک `ManagedMediaSource` جدید می‌سازد، آن را به یک عنصر {{htmlelement("video")}} متصل می‌کند، و از رویداد {{domxref("ManagedMediaSource.startstreaming_event", "startstreaming")}} برای شروع واکشی داده‌های رسانه استفاده می‌کند.

```js
const videoUrl =
  "https://mdn.github.io/shared-assets/videos/flower-fragmented.mp4";
const mediaType = 'video/mp4; codecs="avc1.64001F, mp4a.40.2"';

if (ManagedMediaSource.isTypeSupported(mediaType)) {
  const source = new ManagedMediaSource();
  const video = document.createElement("video");

  video.controls = true;
  video.disableRemotePlayback = true;
  video.src = URL.createObjectURL(source);
  document.body.appendChild(video);

  source.addEventListener("sourceopen", () => {
    const sourceBuffer = source.addSourceBuffer(mediaType);

    source.addEventListener("startstreaming", async () => {
      console.log("startstreaming — fetching media data");
      const response = await fetch(videoUrl);
      const data = await response.arrayBuffer();
      sourceBuffer.appendBuffer(data);
    });
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ManagedMediaSource")}}
- {{domxref("ManagedSourceBuffer")}}
- {{domxref("MediaSource.MediaSource", "MediaSource()")}}