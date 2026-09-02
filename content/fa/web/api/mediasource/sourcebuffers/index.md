---
title: "MediaSource: sourceBuffers property"
short-title: sourceBuffers
slug: Web/API/MediaSource/sourceBuffers
page-type: web-api-instance-property
browser-compat: api.MediaSource.sourceBuffers
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‌خواندنی **`sourceBuffers`** از رابط {{domxref("MediaSource")}} یک شیء {{domxref("SourceBufferList")}} برمی‌گرداند که شامل لیستی از اشیاء {{domxref("SourceBuffer")}} مرتبط با این `MediaSource` است.

## مقدار

یک {{domxref("SourceBufferList")}}.

## مثال‌ها

قطعه کد زیر بر اساس مثالی نوشته شده توسط Nick Desaulniers است ([نمایش نمایش زنده کامل](https://nickdesaulniers.github.io/netfix/demo/bufferAll.html) یا [دانلود سورس](https://github.com/nickdesaulniers/netfix/blob/gh-pages/demo/bufferAll.html) برای بررسی بیشتر). تابع `getMediaSource()` که در اینجا تعریف نشده است، یک `MediaSource` برمی‌گرداند.

```js
const mediaSource = getMediaSource();

function sourceOpen() {
  console.log(this.readyState); // open
  const sourceBuffer = mediaSource.addSourceBuffer(mimeCodec);
  fetchAB(assetURL, (buf) => {
    sourceBuffer.addEventListener("updateend", () => {
      mediaSource.endOfStream();
      console.log(mediaSource.sourceBuffers); // will contain the source buffer that was added above
      video.play();
      console.log(mediaSource.readyState); // ended
    });
    sourceBuffer.appendBuffer(buf);
  });
}

// …
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SourceBuffer")}}
- {{domxref("SourceBufferList")}}