---
title: "ManagedSourceBuffer"
slug: Web/API/ManagedSourceBuffer
page-type: web-api-interface
status:
  - experimental
browser-compat: api.ManagedSourceBuffer
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}{{SeeCompatTable}}

رابطهٔ **`ManagedSourceBuffer`** در {{domxref("Media Source Extensions API", "Media Source Extensions API", "", "nocode")}} یک {{domxref("SourceBuffer")}} است که توسط یک {{domxref("ManagedMediaSource")}} هنگام فراخوانی {{domxref("MediaSource.addSourceBuffer", "addSourceBuffer()")}} ساخته می‌شود. این رابط همهٔ ویژگی‌ها و روش‌های `SourceBuffer` را به ارث می‌برد و علاوه بر آن، هر زمان که محدوده‌های بافر تغییر کنند — از جمله هنگامی که عامل کاربر (user agent) به‌عنوان بخشی از الگوریتم پاک‌سازی حافظهٔ خود محتوا را بیرون می‌ریزد — یک رویداد {{domxref("ManagedSourceBuffer.bufferedchange_event", "bufferedchange")]] را فعال می‌کند.

برنامه‌ها باید برای پیگیری تغییرات دادهٔ بافر شده به رویداد `bufferedchange` گوش دهند، زیرا یک `ManagedMediaSource` ممکن است در هر زمان به دلایلی مانند محدودیت‌های حافظه یا سخت‌افزار، محتوا را بیرون بریزد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از رابط والد خود، {{domxref("SourceBuffer")}}، به ارث می‌برد._

## روش‌های نمونه

_روش‌ها را از رابط والد خود، {{domxref("SourceBuffer")}}، به ارث می‌برد._

## رویدادها

_همچنین رویدادها را از رابط والد خود، {{domxref("SourceBuffer")}}، به ارث می‌برد._

- {{domxref("ManagedSourceBuffer.bufferedchange_event", "bufferedchange")}} {{experimental_inline}}
  - : هنگامی که محدودهٔ بافرِ `ManagedSourceBuffer` تغییر می‌کند، پس از فراخوانی {{domxref("SourceBuffer.appendBuffer", "appendBuffer()")}}، {{domxref("SourceBuffer.remove", "remove()")}}، {{domxref("MediaSource.endOfStream", "endOfStream()")}}، یا در نتیجهٔ اجرای الگوریتم پاک‌سازی حافظه توسط عامل کاربر، فعال می‌شود.

## مثال‌ها

### گوش دادن به تغییرات محدودهٔ بافر

این مثال یک {{domxref("ManagedMediaSource")}} تنظیم می‌کند، یک `ManagedSourceBuffer` اضافه می‌کند، یک فایل MP4 خردشده (fragmented) را واکشی می‌کند و برای ثبت هر تغییری در محدوده‌های بافر، به رویداد `bufferedchange` گوش می‌دهد.

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

  source.addEventListener("sourceopen", async () => {
    const sourceBuffer = source.addSourceBuffer(mediaType);

    sourceBuffer.addEventListener("bufferedchange", (event) => {
      for (let i = 0; i < event.addedRanges.length; i++) {
        console.log(
          `Added: ${event.addedRanges.start(i)}s - ${event.addedRanges.end(i)}s`,
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
- {{domxref("BufferedChangeEvent")}}
- {{domxref("SourceBuffer")}}
- {{domxref("MediaSource")}}