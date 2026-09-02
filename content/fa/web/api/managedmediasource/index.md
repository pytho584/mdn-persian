---
title: ManagedMediaSource
slug: Web/API/ManagedMediaSource
page-type: web-api-interface
status:
  - experimental
browser-compat: api.ManagedMediaSource
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}{{SeeCompatTable}}

رابط **`ManagedMediaSource`** از {{domxref("Media Source Extensions API", "Media Source Extensions API", "", "nocode")}} یک {{domxref("MediaSource")}} است که محتوای حافظه‌ی خود را به‌شکل فعال مدیریت می‌کند. برخلاف `MediaSource` معمولی، عامل کاربر می‌تواند در هر زمان، به دلایلی مانند محدودیت‌های حافظه یا سخت‌افزار، محتوا را از اشیاء {{domxref("ManagedSourceBuffer")}} خود حذف کند. این موضوع آن را برای سناریوهای پخش جریانی کم‌مصرف که در آن‌ها عامل کاربر به کنترل بیشتری روی داده‌های رسانه‌ای بافر شده نیاز دارد، مناسب می‌سازد.

وقتی {{domxref("MediaSource.addSourceBuffer", "addSourceBuffer()")}} روی یک `ManagedMediaSource` فراخوانی می‌شود، به‌جای اشیاء {{domxref("SourceBuffer")}} اشیاء {{domxref("ManagedSourceBuffer")}} ایجاد می‌کند. این اشیاء رویدادهای {{domxref("ManagedSourceBuffer.bufferedchange_event", "bufferedchange")}} را فعال می‌کنند تا زمانی که عامل کاربر محدوده‌های بافر شده را تغییر می‌دهد، برنامه از این تغییر مطلع شود.

> [!NOTE]
> در Safari، `ManagedMediaSource` فقط زمانی فعال می‌شود که پخش از راه دور (remote playback) به‌طور صریح روی عنصر رسانه‌ای غیرفعال شده باشد (با تنظیم {{domxref("HTMLMediaElement.disableRemotePlayback")}} روی `true`)، یا زمانی که یک منبع جایگزین AirPlay ارائه شده باشد (برای مثال، یک عنصر {{htmlelement("source")}} از نوع HLS). بدون هریک از این موارد، رویداد {{domxref("MediaSource.sourceopen_event", "sourceopen")}} فعال نخواهد شد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("ManagedMediaSource.ManagedMediaSource", "ManagedMediaSource()")}} {{experimental_inline}}
  - : یک نمونه‌ی شیء جدید `ManagedMediaSource` بدون هیچ بافر منبع مرتبط ایجاد می‌کند و برمی‌گرداند.

## ویژگی‌های نمونه

_همچنین ویژگی‌های رابط والد خود، {{domxref("MediaSource")}}، را به ارث می‌گیرد._

- {{domxref("ManagedMediaSource.streaming")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک مقدار بولین که نشان می‌دهد آیا شیء `ManagedMediaSource` در حال حاضر در حال پخش جریانی است یا نه. وقتی `true` باشد، برنامه باید به‌طور فعال داده‌های رسانه‌ای را دریافت کرده و به بافر اضافه کند. وقتی `false` باشد، برنامه می‌تواند دریافت داده‌های جدید را متوقف کند.

## متدهای نمونه

_متدهای رابط والد خود، {{domxref("MediaSource")}}، را به ارث می‌گیرد._

## رویدادها

_همچنین رویدادهای رابط والد خود، {{domxref("MediaSource")}}، را به ارث می‌گیرد._

- {{domxref("ManagedMediaSource.startstreaming_event", "startstreaming")}} {{experimental_inline}}
  - : وقتی فعال می‌شود که ویژگی {{domxref("ManagedMediaSource.streaming", "streaming")}} متعلق به `ManagedMediaSource` از `false` به `true` تغییر کند؛ یعنی منبع رسانه‌ای پخش جریانی را آغاز کرده است.
- {{domxref("ManagedMediaSource.endstreaming_event", "endstreaming")}} {{experimental_inline}}
  - : وقتی فعال می‌شود که ویژگی {{domxref("ManagedMediaSource.streaming", "streaming")}} متعلق به `ManagedMediaSource` از `true` به `false` تغییر کند؛ یعنی منبع رسانه‌ای پخش جریانی را متوقف کرده است.

## مثال‌ها

### راه‌اندازی یک منبع رسانه‌ای مدیریت‌شده

مثال زیر یک `ManagedMediaSource` راه‌اندازی می‌کند، آن را به یک عنصر {{htmlelement("video")}} متصل می‌کند و به رویدادهای {{domxref("ManagedMediaSource.startstreaming_event", "startstreaming")}} و {{domxref("ManagedMediaSource.endstreaming_event", "endstreaming")}} گوش می‌دهد تا زمان دریافت داده‌های رسانه‌ای را کنترل کند. رویدادهای {{domxref("ManagedSourceBuffer.bufferedchange_event", "bufferedchange")}} نیز در زیر ویدیو ثبت می‌شوند.

```js
const videoUrl =
  "https://mdn.github.io/shared-assets/videos/flower-fragmented.mp4";
const mediaType = 'video/mp4; codecs="avc1.64001F, mp4a.40.2"';
const video = document.querySelector("video");

if (!window.ManagedMediaSource?.isTypeSupported(mediaType)) {
  console.log("ManagedMediaSource is not supported in this browser.");
} else {
  const source = new ManagedMediaSource();
  video.disableRemotePlayback = true;
  video.src = URL.createObjectURL(source);

  source.addEventListener("sourceopen", () => {
    const sourceBuffer = source.addSourceBuffer(mediaType);

    sourceBuffer.addEventListener("bufferedchange", (event) => {
      for (let i = 0; i < event.addedRanges.length; i++) {
        console.log(
          `Buffered: ${event.addedRanges.start(i).toFixed(2)}s – ${event.addedRanges.end(i).toFixed(2)}s`,
        );
      }
    });

    source.addEventListener("startstreaming", async () => {
      console.log("startstreaming — fetching media data…");
      const response = await fetch(videoUrl);
      const data = await response.arrayBuffer();
      sourceBuffer.appendBuffer(data);
    });

    source.addEventListener("endstreaming", () => {
      console.log("endstreaming — enough data buffered");
    });
  });
}
```

{{EmbedGHLiveSample("dom-examples/media-source-extensions/managed-media-source/", '100%', 470)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MediaSource")}}
- {{domxref("ManagedSourceBuffer")}}
- {{domxref("BufferedChangeEvent")}}
- {{domxref("SourceBuffer")}}