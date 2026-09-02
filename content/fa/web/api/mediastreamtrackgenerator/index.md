---
title: MediaStreamTrackGenerator
slug: Web/API/MediaStreamTrackGenerator
page-type: web-api-interface
status:
  - experimental
  - non-standard
browser-compat: api.MediaStreamTrackGenerator
---

{{APIRef("Insertable Streams for MediaStreamTrack API")}}{{SeeCompatTable}}{{Non-standard_Header}}

> [!NOTE]
> به‌جای آن از {{domxref("VideoTrackGenerator")}} استفاده کنید.

رابط **`MediaStreamTrackGenerator`** در [API جریان‌های قابل درج برای MediaStreamTrack](/en-US/docs/Web/API/Insertable_Streams_for_MediaStreamTrack_API) یک {{domxref("WritableStream")}} ایجاد می‌کند که به‌عنوان منبع {{domxref("MediaStreamTrack")}} عمل می‌کند.
این شیء یک جریان از فریم‌های رسانه‌ای را به‌عنوان ورودی مصرف می‌کند که می‌تواند فریم‌های صوتی یا تصویری باشد.

## سازنده

- {{domxref("MediaStreamTrackGenerator.MediaStreamTrackGenerator", "MediaStreamTrackGenerator()")}} {{Experimental_Inline}} {{Non-standard_Inline}}
  - : یک شیء `MediaStreamTrackGenerator` جدید ایجاد می‌کند که اشیاء {{domxref("VideoFrame")}} یا {{domxref("AudioData")}} را می‌پذیرد.

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌های {{domxref("MediaStreamTrack")}} را به ارث می‌برد._

- {{domxref("MediaStreamTrackGenerator.writable")}} {{Experimental_Inline}} {{Non-standard_Inline}}
  - : یک {{domxref("WritableStream")}}.

## روش‌های نمونه

_این رابط هیچ روش خاصی را پیاده‌سازی نمی‌کند، اما روش‌های {{domxref("MediaStreamTrack")}} را به ارث می‌برد._

## مثال‌ها

مثال زیر از مقاله [جریان‌های قابل درج برای MediaStreamTrack](https://developer.chrome.com/docs/capabilities/web-apis/mediastreamtrack-insertable-media-processing) گرفته شده است و یک برنامه اسکنر بارکد را نشان می‌دهد که بارکدها را پردازش و برجسته می‌کند و سپس فریم‌های تبدیل‌شده را به جریان نوشتنی {{domxref("MediaStreamTrackGenerator.writable")}} می‌نویسد.

```js
const stream = await getUserMedia({ video: true });
const videoTrack = stream.getVideoTracks()[0];

const trackProcessor = new MediaStreamTrackProcessor({ track: videoTrack });
const trackGenerator = new MediaStreamTrackGenerator({ kind: "video" });

const transformer = new TransformStream({
  async transform(videoFrame, controller) {
    const barcodes = await detectBarcodes(videoFrame);
    const newFrame = highlightBarcodes(videoFrame, barcodes);
    videoFrame.close();
    controller.enqueue(newFrame);
  },
});

trackProcessor.readable
  .pipeThrough(transformer)
  .pipeTo(trackGenerator.writable);
```

## همچنین ببینید

- {{domxref("VideoTrackGenerator")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}