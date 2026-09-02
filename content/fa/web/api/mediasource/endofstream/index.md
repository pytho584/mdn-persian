---
title: "MediaSource: endOfStream() method"
short-title: endOfStream()
slug: Web/API/MediaSource/endOfStream
page-type: web-api-instance-method
browser-compat: api.MediaSource.endOfStream
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`endOfStream()`** از رابط {{domxref("MediaSource")}} پایان جریان را اعلام می‌کند.

## نحو (Syntax)

```js-nolint
endOfStream()
endOfStream(endOfStreamError)
```

### پارامترها

- `endOfStreamError` {{optional_inline}}
  - : یک رشته که خطایی را برای پرتاب کردن هنگام رسیدن به پایان جریان مشخص می‌کند. مقادیر ممکن عبارتند از:
    - `network`
      - : پخش را خاتمه می‌دهد و اعلام می‌کند که یک خطای شبکه رخ داده است. این می‌تواند برای ایجاد یک کنترل‌کننده خطای سفارشی مرتبط با جریان‌های رسانه‌ای استفاده شود. به عنوان مثال، ممکن است تابعی داشته باشید که درخواست‌های تکه‌های رسانه را جدا از سایر درخواست‌های شبکه مدیریت می‌کند. هنگامی که یک درخواست {{domxref("Window/fetch", "fetch()")}} برای یک تکه رسانه انجام می‌دهید و با خطای شبکه مواجه می‌شوید، ممکن است بخواهید `endOfStream('network')` را فراخوانی کنید، یک پیام توصیفی در رابط کاربری نمایش دهید، و شاید بلافاصله درخواست شبکه را مجدداً امتحان کنید یا تا زمانی که شبکه دوباره وصل شود (از طریق نوعی نظرسنجی) صبر کنید.
    - `decode`
      - : پخش را خاتمه می‌دهد و اعلام می‌کند که یک خطای رمزگشایی رخ داده است. این می‌تواند برای نشان دادن این که در هنگام واکشی داده‌های رسانه یک خطای تجزیه رخ داده است استفاده شود؛ ممکن است داده‌ها خراب باشند، یا با استفاده از یک کدک که مرورگر نحوه رمزگشایی آن را نمی‌داند، رمزگذاری شده باشند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("MediaSource.readyState")}} برابر با `open` نباشد، یا یک یا چند شیء {{domxref("SourceBuffer")}} در {{domxref("MediaSource.sourceBuffers")}} در حال به‌روزرسانی باشند (یعنی خاصیت {{domxref("SourceBuffer.updating")}} آنها `true` باشد)، پرتاب می‌شود.

## مثال‌ها

قطعه کد زیر از یک مثال نوشته شده توسط Nick Desaulniers گرفته شده است ([مشاهده دموی کامل به صورت زنده](https://nickdesaulniers.github.io/netfix/demo/bufferAll.html)، یا [دانلود سورس](https://github.com/nickdesaulniers/netfix/blob/gh-pages/demo/bufferAll.html) برای بررسی بیشتر). تابع `getMediaSource()` که در اینجا تعریف نشده است، یک `MediaSource` برمی‌گرداند.

```js
const assetURL = "frag_bunny.mp4";
// Need to be specific for Blink regarding codecs
// ./mp4info frag_bunny.mp4 | grep Codec
const mimeCodec = 'video/mp4; codecs="avc1.42E01E, mp4a.40.2"';

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SourceBuffer")}}
- {{domxref("SourceBufferList")}}