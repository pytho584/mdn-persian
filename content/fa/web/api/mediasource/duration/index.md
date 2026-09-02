---
title: "MediaSource: duration property"
short-title: duration
slug: Web/API/MediaSource/duration
page-type: web-api-instance-property
browser-compat: api.MediaSource.duration
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی **`duration`** در interface {{domxref("MediaSource")}} مدت‌زمان رسانه‌ای را که در حال حاضر نمایش داده می‌شود، می‌خواند و تنظیم می‌کند.

## مقدار

یک عدد اعشاری (double). مقدار بر حسب ثانیه انتظار می‌رود.

### استثناها

هنگام تنظیم مقدار جدید برای این ویژگی، ممکن است استثناهای زیر پرتاب شوند.

- `InvalidAccessError` {{domxref("DOMException")}}
  - : اگر تلاش شود مقدار duration منفی یا `NaN` تنظیم شود، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("MediaSource.readyState")}} برابر با `open` نباشد، یا یک یا چند شیء {{domxref("SourceBuffer")}} در {{domxref("MediaSource.sourceBuffers")}} در حال به‌روزرسانی باشند (یعنی ویژگی {{domxref("SourceBuffer.updating")}} آن‌ها `true` باشد)، پرتاب می‌شود.

## مثال‌ها

قطعه کد زیر بر اساس مثالی نوشته‌شده توسط Nick Desaulniers است ([مشاهده دموی کامل به‌صورت زنده](https://nickdesaulniers.github.io/netfix/demo/bufferAll.html)، یا [دانلود سورس](https://github.com/nickdesaulniers/netfix/blob/gh-pages/demo/bufferAll.html) برای بررسی بیشتر). تابع `getMediaSource()` که در اینجا تعریف نشده است، یک `MediaSource` برمی‌گرداند.

```js
const mediaSource = getMediaSource();

function sourceOpen() {
  console.log(this.readyState); // open
  const sourceBuffer = mediaSource.addSourceBuffer(mimeCodec);
  fetchAB(assetURL, (buf) => {
    sourceBuffer.addEventListener("updateend", () => {
      mediaSource.endOfStream();
      mediaSource.duration = 120;
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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SourceBuffer")}}
- {{domxref("SourceBufferList")}}