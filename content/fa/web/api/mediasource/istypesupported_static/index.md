---
title: "MediaSource: isTypeSupported() static method"
short-title: isTypeSupported()
slug: Web/API/MediaSource/isTypeSupported_static
page-type: web-api-static-method
browser-compat: api.MediaSource.isTypeSupported_static
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

متد ایستای **`MediaSource.isTypeSupported()`** یک مقدار بولین برمی‌گرداند که اگر نوع MIME داده‌شده و (به‌صورت اختیاری) codec مربوطه _به احتمال زیاد_ توسط {{Glossary("user agent")}} فعلی پشتیبانی می‌شود، برابر با `true` است.

به بیان دیگر، اگر بتواند برای آن نوع رسانه، آبجکت‌های {{domxref("SourceBuffer")}} را با موفقیت ایجاد کند.
اگر مقدار برگشتی `false` باشد، به این معنی است که user agent مطمئن است که _نمی‌تواند_ به رسانه‌ای با قالب مشخص‌شده دسترسی داشته باشد.

## Syntax

```js-nolint
MediaSource.isTypeSupported(type)
```

### Parameters

- `type`
  - : رشته‌ای که نوع MIME رسانه و (به‌صورت اختیاری) یک [`codecs` parameter](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter) شامل فهرستی از codecهای پشتیبانی‌شده را که با کاما از هم جدا شده‌اند، مشخص می‌کند.

### Return value

اگر رسانه با نوع داده‌شده _پخش نخواهد شد_، مقدار `false` برمی‌گردد.

اگر مرورگر بتواند _احتمالاً_ رسانه‌ای با نوع مشخص‌شده را پخش کند، مقدار `true` برگردانده می‌شود.
این یک _تضمین_ نیست و کد شما باید برای این احتمال آماده باشد که رسانه به‌درستی پخش نشود یا اصلاً پخش نشود.

همه APIهای وب که با فایل‌های رسانه‌ای کار می‌کنند، هنگام تعیین اینکه آیا می‌توان از یک نوع رسانه استفاده کرد، از رویکرد «نه/شاید/احتمالاً» (یا در این مورد، «نه یا احتمالاً») استفاده می‌کنند.
دلیل این امر آن است که فایل‌های رسانه‌ای ساختارهای پیچیده و ظریفی هستند و تنوعات بسیار ریز و متعددی دارند تا زمانی که واقعاً از محتوای رسانه استفاده نکنید، نتوان در مورد هیچ‌چیز کاملاً مطمئن بود.

## Examples

قطعه کد زیر از مثالی نوشته‌شده توسط Nick Desaulniers گرفته شده است ([مشاهده دموی کامل](https://nickdesaulniers.github.io/netfix/demo/bufferAll.html) یا [دانلود سورس](https://github.com/nickdesaulniers/netfix/blob/gh-pages/demo/bufferAll.html) برای بررسی بیشتر). تابع `getMediaSource()` که در اینجا تعریف نشده است، یک `MediaSource` برمی‌گرداند.

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

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Media Source Extensions API](/en-US/docs/Web/API/Media_Source_Extensions_API)
- [Guide to media types and formats on the web](/en-US/docs/Web/Media/Guides/Formats)
- [Codecs in common media types](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter)
- {{domxref("SourceBuffer")}}
- {{domxref("SourceBufferList")}}