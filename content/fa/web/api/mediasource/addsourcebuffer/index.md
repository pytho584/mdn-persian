---
title: "MediaSource: addSourceBuffer() method"
short-title: addSourceBuffer()
slug: Web/API/MediaSource/addSourceBuffer
page-type: web-api-instance-method
browser-compat: api.MediaSource.addSourceBuffer
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`addSourceBuffer()`** از رابط {{domxref("MediaSource")}} یک {{domxref("SourceBuffer")}} جدید با {{Glossary("MIME type")}} مشخص‌شده می‌سازد و آن را به فهرست {{domxref("MediaSource.sourceBuffers", "sourceBuffers")}} متعلق به `MediaSource` اضافه می‌کند. سپس `SourceBuffer` جدید نیز بازگردانده می‌شود.

## نحو (Syntax)

```js-nolint
addSourceBuffer(mimeType)
```

### پارامترها

- `mimeType`
  - : یک رشته (string) که نوع MIME مربوط به {{domxref("SourceBuffer")}} موردنظر برای ایجاد و افزودن به {{domxref("MediaSource")}} را مشخص می‌کند.

### مقدار بازگشتی

یک شیء {{domxref("SourceBuffer")}} که نشان‌دهندهٔ بافر منبع (source buffer) جدید ایجادشده و افزوده‌شده به منبع رسانه‌ای است.

### استثناها (Exceptions)

- `InvalidAccessError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که مقدار ارائه‌شده برای `mimeType` یک رشتهٔ خالی باشد، نه یک نوع MIME معتبر.
- `InvalidStateError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که {{domxref("MediaSource")}} در وضعیت `"open"` متعلق به {{domxref("MediaSource.readyState", "readyState")}} نباشد.
- `NotSupportedError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که `mimeType` مشخص‌شده توسط {{Glossary("user agent")}} پشتیبانی نشود، یا با انواع MIME سایر اشیاء {{domxref("SourceBuffer")}} که از قبل در فهرست {{domxref("MediaSource.sourceBuffers", "sourceBuffers")}} منبع رسانه‌ای قرار دارند ناسازگار باشد.
- {{domxref("QuotaExceededError")}}
  - : زمانی پرتاب می‌شود که user agent قادر به مدیریت اشیاء `SourceBuffer` بیشتری نباشد، یا ایجاد یک `SourceBuffer` جدید با استفاده از `mimeType` داده‌شده منجر به [پیکربندی پشتیبانی‌نشده از `SourceBuffer`ها](https://w3c.github.io/media-source/#sourcebuffer-configuration) شود.

## مثال‌ها

قطعه کد زیر از یک مثال نوشته‌شده توسط Nick Desaulniers گرفته شده است ([مشاهدهٔ نسخهٔ کامل آزمایشی به‌صورت زنده](https://nickdesaulniers.github.io/netfix/demo/bufferAll.html)، یا [دانلود کد منبع](https://github.com/nickdesaulniers/netfix/blob/gh-pages/demo/bufferAll.html) برای بررسی بیشتر). تابع `getMediaSource()` که در اینجا تعریف نشده است، یک `MediaSource` برمی‌گرداند.

```js
const assetURL = "frag_bunny.mp4";
// Need to be specific for Blink regarding codecs
// ./mp4info frag_bunny.mp4 | grep Codec
const mimeCodec = 'video/mp4; codecs="avc1.42E01E, mp4a.40.2"';
const mediaSource = getMediaSource();

if ("MediaSource" in window && MediaSource.isTypeSupported(mimeCodec)) {
  console.log(mediaSource.readyState); // closed
  mediaSource.addEventListener("sourceopen", sourceOpen);
  video.src = URL.createObjectURL(mediaSource);
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

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("SourceBuffer")}}
- {{domxref("SourceBufferList")}}