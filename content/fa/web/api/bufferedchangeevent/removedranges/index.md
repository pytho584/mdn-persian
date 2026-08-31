---
title: "BufferedChangeEvent: removedRanges property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BufferedChangeEvent/removedRanges"
translated_by: "n8n + AI"
---

---
title: "BufferedChangeEvent: removedRanges property"
short-title: removedRanges
slug: Web/API/BufferedChangeEvent/removedRanges
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.BufferedChangeEvent.removedRanges
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}{{SeeCompatTable}}

خاصیت فقط خواندنی **`removedRanges`** از رابط {{domxref("BufferedChangeEvent")}} یک شیء {{domxref("TimeRanges")}} را برمی‌گرداند که بازه‌های زمانی حذف شده از {{domxref("ManagedSourceBuffer")}} مرتبط را نشان می‌دهد. این بازه‌ها بین آخرین رویدادهای `updatestart` و `updateend`، در طول آخرین اجرای الگوریتم حذف فریم کدگذاری شده یا الگوریتم تخلیه فریم کدگذاری شده، یا در نتیجه اجرای الگوریتم پاکسازی حافظه توسط عامل کاربر حذف شده‌اند.

## مقدار

یک شیء {{domxref("TimeRanges")}}.

## مثال‌ها

### ثبت بازه‌های حذف شده در تغییر بافر

این مثال یک {{domxref("ManagedMediaSource")}} ایجاد می‌کند، آن را به یک عنصر {{htmlelement("video")}} متصل می‌کند، یک فایل MP4 تکه‌تکه شده را واکشی می‌کند، و سپس بخشی از داده‌های بافر شده را حذف می‌کند. کنترل‌کننده رویداد `bufferedchange` هر بازه زمانی حذف شده را ثبت می‌کند.

```js
const videoUrl =
  "https://mdn.github.io/shared-assets/videos/flower-fragmented.mp4";
const mediaType = 'video/mp4; codecs="avc1.64001F, mp4a.40.2"';

if (ManagedMediaSource.isTypeSupported(mediaType)) {
  const video = document.createElement("video");
  const source = new ManagedMediaSource();

  video.controls = true;
  video.disableRemotePlayback = true;
  video.src = URL.createObjectURL(source);
  document.body.appendChild(video);

  source.addEventListener("sourceopen", async () => {
    const sourceBuffer = source.addSourceBuffer(mediaType);

    sourceBuffer.addEventListener("bufferedchange", (event) => {
      const removed = event.removedRanges;
      for (let i = 0; i < removed.length; i++) {
        console.log(`Removed range: ${removed.start(i)}s - ${removed.end(i)}s`);
      }
    });

    const response = await fetch(videoUrl);
    const data = await response.arrayBuffer();
    sourceBuffer.appendBuffer(data);

    // Once appended, remove the first 5 seconds to trigger removedRanges
    sourceBuffer.addEventListener(
      "updateend",
      () => {
        sourceBuffer.remove(0, 5);
      },
      { once: true },
    );
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("BufferedChangeEvent.addedRanges")}}
- {{domxref("ManagedSourceBuffer.bufferedchange_event", "bufferedchange")}} event
- {{domxref("ManagedSourceBuffer")}}
- {{domxref("TimeRanges")}}