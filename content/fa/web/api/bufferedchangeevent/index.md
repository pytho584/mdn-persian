---
title: "BufferedChangeEvent"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BufferedChangeEvent"
translated_by: "n8n + AI"
---

---
title: BufferedChangeEvent
slug: Web/API/BufferedChangeEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BufferedChangeEvent
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}{{SeeCompatTable}}

رابط **`BufferedChangeEvent`** از {{domxref("Media Source Extensions API", "Media Source Extensions API", "", "nocode")}}، شیء رویداد مربوط به رویداد {{domxref("ManagedSourceBuffer.bufferedchange_event", "bufferedchange")}} را نشان می‌دهد که روی یک {{domxref("ManagedSourceBuffer")}} شلیک می‌شود. این رویداد هر زمان که محدوده‌های بافرشده‌ی `ManagedSourceBuffer` تغییر کنند، برای مثال در نتیجه‌ی فراخوانی‌های {{domxref("SourceBuffer.appendBuffer", "appendBuffer()")}}، {{domxref("SourceBuffer.remove", "remove()")}} یا {{domxref("MediaSource.endOfStream", "endOfStream()")}}، یا زمانی که عامل کاربر (user agent) الگوریتم پاک‌سازی حافظه را اجرا می‌کند، شلیک می‌شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("BufferedChangeEvent.BufferedChangeEvent", "BufferedChangeEvent()")}} {{experimental_inline}}
  - : یک شیء `BufferedChangeEvent` جدید ایجاد کرده و آن را برمی‌گرداند.

## ویژگی‌های نمونه

_همچنین ویژگی‌های رابط والد خود، {{domxref("Event")}} را به ارث می‌برد._

- {{domxref("BufferedChangeEvent.addedRanges")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک شیء {{domxref("TimeRanges")}} که بازه‌های زمانی اضافه‌شده به بافر {{domxref("ManagedSourceBuffer")}} را نشان می‌دهد.
- {{domxref("BufferedChangeEvent.removedRanges")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک شیء {{domxref("TimeRanges")}} که بازه‌های زمانی حذف‌شده از بافر {{domxref("ManagedSourceBuffer")}} را نشان می‌دهد.

## مثال‌ها

این مثال یک {{domxref("ManagedMediaSource")}} می‌سازد، آن را به یک عنصر {{htmlelement("video")}} متصل می‌کند، یک فایل MP4 تکه‌تکه‌شده را دریافت می‌کند، و به رویداد `bufferedchange` گوش می‌دهد. وقتی رویداد شلیک می‌شود، بازه‌های زمانی اضافه‌شده را در کنسول ثبت می‌کند.

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
      for (let i = 0; i < event.addedRanges.length; i++) {
        console.log(
          `Added range: ${event.addedRanges.start(i)} - ${event.addedRanges.end(i)}`,
        );
      }
    });

    const response = await fetch(videoUrl);
    const data = await response.arrayBuffer();
    sourceBuffer.appendBuffer(data);
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
- {{domxref("MediaSource")}}
- {{domxref("SourceBuffer")}}