---
title: "ManagedSourceBuffer: bufferedchange event"
short-title: bufferedchange
slug: Web/API/ManagedSourceBuffer/bufferedchange_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.ManagedSourceBuffer.bufferedchange_event
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}{{SeeCompatTable}}

رویداد **`bufferedchange`** از رابط {{domxref("ManagedSourceBuffer")}} زمانی فعال میشود که محدودهٔ بافرشدهٔ `ManagedSourceBuffer` تغییر کند. این اتفاق میتواند پس از فراخوانی {{domxref("SourceBuffer.appendBuffer", "appendBuffer()")}}، {{domxref("SourceBuffer.remove", "remove()")}} یا {{domxref("MediaSource.endOfStream", "endOfStream()")}} رخ دهد، یا در نتیجهٔ اجرای الگوریتم پاکسازی حافظه توسط عامل کاربر (user agent) ایجاد شود.

این رویداد برای برنامههایی که از {{domxref("ManagedMediaSource")}} استفاده میکنند اهمیت دارد، زیرا عامل کاربر میتواند در هر زمان محتوای بافرشده را حذف کند. با گوش دادن به این رویداد، برنامهها میتوانند متوجه شوند که دادهٔ بافرشده حذف شده است و با واکشی بخشهای جایگزین، از توقف پخش جلوگیری کنند.

## نحو (Syntax)

برای استفاده از نام رویداد در روشهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم ویژگی مدیریتکنندهٔ رویداد، میتوانید به شکل زیر عمل کنید:

```js-nolint
addEventListener("bufferedchange", (event) => {});

onbufferedchange = (event) => {};
```

## نوع رویداد

یک {{domxref("BufferedChangeEvent")}} که از {{domxref("Event")}} ارث میبرد.

{{InheritanceDiagram("BufferedChangeEvent")}}

## مثالها

### ردیابی تغییرات محدودهٔ بافرشده

در این مثال، یک {{domxref("ManagedMediaSource")}} راهاندازی میشود، یک بافر منبع اضافه میگردد، یک فایل MP4 تکهتکهشده واکشی میشود، و با گوش دادن به رویداد `bufferedchange` هر تغییر در محدودههای بافرشده ثبت میشود.

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
      for (let i = 0; i < event.removedRanges.length; i++) {
        console.log(
          `Removed: ${event.removedRanges.start(i)}s - ${event.removedRanges.end(i)}s`,
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

- {{domxref("BufferedChangeEvent")}}
- {{domxref("ManagedMediaSource")}}
- {{domxref("ManagedSourceBuffer")}}
- {{domxref("SourceBuffer")}}