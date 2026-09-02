---
title: "MediaSource: readyState property"
short-title: readyState
slug: Web/API/MediaSource/readyState
page-type: web-api-instance-property
browser-compat: api.MediaSource.readyState
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

خاصیت فقط خواندنی **`readyState`** در رابط {{domxref("MediaSource")}} یک enum (شمارشی) را برمی‌گرداند که وضعیت `MediaSource` جاری را نشان می‌دهد. سه مقدار ممکن عبارتند از:

- `closed`: منبع در حال حاضر به یک عنصر رسانه‌ای متصل نیست.
- `open`: منبع به یک عنصر رسانه‌ای متصل است و آماده دریافت اشیاء {{domxref("SourceBuffer")}} می‌باشد.
- `ended`: منبع به یک عنصر رسانه‌ای متصل است اما جریان با فراخوانی {{domxref("MediaSource.endOfStream()")}} پایان یافته است.

## مقدار

یک رشته.

## مثال‌ها

قطعه کد زیر از یک مثال نوشته شده توسط Nick Desaulniers گرفته شده است ([مشاهده دموی کامل زنده](https://nickdesaulniers.github.io/netfix/demo/bufferAll.html)، یا [دانلود سورس](https://github.com/nickdesaulniers/netfix/blob/gh-pages/demo/bufferAll.html) برای بررسی بیشتر). تابع `getMediaSource()` که در اینجا تعریف نشده است، یک `MediaSource` برمی‌گرداند.

```js
let mediaSource;

if ("MediaSource" in window && MediaSource.isTypeSupported(mimeCodec)) {
  mediaSource = getMediaSource();
  console.log(mediaSource.readyState); // closed
  video.src = URL.createObjectURL(mediaSource);
  mediaSource.addEventListener("sourceopen", sourceOpen);
} else {
  console.error("Unsupported MIME type or codec: ", mimeCodec);
}

function sourceOpen() {
  console.log(this.readyState); // open
  const sourceBuffer = mediaSource.addSourceBuffer(mimeCodec);
  fetchAB(assetURL, (buf) => {
    sourceBuffer.addEventListener("updateend", () => {
      mediaSource.endOfStream();
      video.play();
      console.log(mediaSource.readyState); // ended
    });
    sourceBuffer.appendBuffer(buf);
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SourceBuffer")}}
- {{domxref("SourceBufferList")}}