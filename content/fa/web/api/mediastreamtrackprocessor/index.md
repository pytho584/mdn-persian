---
title: MediaStreamTrackProcessor
slug: Web/API/MediaStreamTrackProcessor
page-type: web-api-interface
browser-compat: api.MediaStreamTrackProcessor
---

{{APIRef("Insertable Streams for MediaStreamTrack API")}}{{AvailableInWorkers("dedicated")}}

> [!WARNING]
> مرورگرها از نظر اینکه این رابط را در کدام بافت سراسری (global context) در دسترس قرار می‌دهند، با هم تفاوت دارند (برای مثال، در برخی مرورگرها فقط در `window` و در برخی دیگر فقط در worker اختصاصی). همین موضوع آن‌ها را ناسازگار می‌کند. هنگام مقایسهٔ پشتیبانی مرورگرها، این نکته را در نظر داشته باشید.

رابط **`MediaStreamTrackProcessor`** از [Insertable Streams for MediaStreamTrack API](/en-US/docs/Web/API/Insertable_Streams_for_MediaStreamTrack_API) منبع یک شیء {{domxref("MediaStreamTrack")}} ویدیویی را مصرف می‌کند و جریانی از اشیاء {{domxref("VideoFrame")}} تولید می‌کند.

## سازنده

- {{domxref("MediaStreamTrackProcessor.MediaStreamTrackProcessor", "MediaStreamTrackProcessor()")}}
  - : یک شیء جدید `MediaStreamTrackProcessor` می‌سازد.
- {{domxref("MediaStreamTrackProcessor.MediaStreamTrackProcessor", "window.MediaStreamTrackProcessor()")}} {{Experimental_Inline}} {{Non-standard_Inline}}
  - : یک شیء جدید `MediaStreamTrackProcessor` روی {{Glossary("main thread")}} می‌سازد که می‌تواند هم ویدیو و هم صدا را پردازش کند.

## ویژگی‌های نمونه

- {{domxref("MediaStreamTrackProcessor.discardedFrames")}} {{experimental_inline}}
  - : عددی که نشان می‌دهد پردازنده چند فریم را کنار گذاشته است.
- {{domxref("MediaStreamTrackProcessor.readable")}}
  - : یک {{domxref("ReadableStream")}} برمی‌گرداند.
- {{domxref("MediaStreamTrackProcessor.totalFrames")}} {{experimental_inline}}
  - : عددی که نشان می‌دهد پردازنده در مجموع چند فریم دریافت کرده است.

## مثال‌ها

مثال زیر از مقالهٔ [Unbundling MediaStreamTrackProcessor and VideoTrackGenerator](https://blog.mozilla.org/webrtc/unbundling-mediastreamtrackprocessor-and-videotrackgenerator/) برداشته شده است. این مثال یک {{domxref("MediaStreamTrack")}} دوربین را برای پردازش به یک worker [انتقال می‌دهد](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects). worker خط لوله‌ای می‌سازد که یک فیلتر سپیا (sepia) روی فریم‌های ویدیو اعمال می‌کند و آن‌ها را آینه‌ای می‌کند. در پایان خط لوله، یک {{domxref("VideoTrackGenerator")}} قرار دارد که {{domxref("MediaStreamTrack")}} آن دوباره به عقب منتقل و پخش می‌شود. بدین ترتیب رسانه در زمان واقعی و خارج از {{Glossary("main thread")}} از این تبدیل عبور می‌کند.

```js
const stream = await navigator.mediaDevices.getUserMedia({ video: true });
const [track] = stream.getVideoTracks();
const worker = new Worker("worker.js");
worker.postMessage({ track }, [track]);
const { data } = await new Promise((r) => {
  worker.onmessage = r;
});
video.srcObject = new MediaStream([data.track]);
```

worker.js:

```js
onmessage = async ({ data: { track } }) => {
  const vtg = new VideoTrackGenerator();
  self.postMessage({ track: vtg.track }, [vtg.track]);
  const { readable } = new MediaStreamTrackProcessor({ track });
  await readable
    .pipeThrough(new TransformStream({ transform }))
    .pipeTo(vtg.writable);
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("VideoTrackGenerator")}}
- [Insertable streams for MediaStreamTrack](https://developer.chrome.com/docs/capabilities/web-apis/mediastreamtrack-insertable-media-processing) در developer.chrome.com
  > [!NOTE]
  > این مقاله پیش از آن‌که این API به workerها و ویدیو محدود شود نوشته شده است. توجه داشته باشید که در آن از نسخهٔ غیراستاندارد `MediaStreamTrackProcessor` استفاده شده است که روی {{Glossary("main thread")}} مسدودکننده است.