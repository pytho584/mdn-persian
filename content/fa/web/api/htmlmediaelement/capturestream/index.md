---
title: "HTMLMediaElement: captureStream() method"
short-title: captureStream()
slug: Web/API/HTMLMediaElement/captureStream
page-type: web-api-instance-method
browser-compat: api.HTMLMediaElement.captureStream
---

{{APIRef("Media Capture and Streams")}}

متد **`captureStream()`** از رابط {{domxref("HTMLMediaElement")}} یک شیء {{domxref('MediaStream')}} برمی‌گرداند که محتوای در حال نمایش در عنصر رسانه را به‌صورت زنده ضبط (stream) می‌کند.

برای مثال، می‌توان از این متد به‌عنوان منبعی برای یک {{domxref("RTCPeerConnection")}} در [WebRTC](/en-US/docs/Web/API/WebRTC_API) استفاده کرد.

## Syntax

```js-nolint
captureStream()
```

### پارامترها

هیچ.

### مقدار برگشتی

یک شیء {{domxref('MediaStream')}} که می‌تواند توسط سایر کدهای پردازش رسانه به‌عنوان منبع داده‌های صوتی و/یا تصویری استفاده شود، یا به‌عنوان منبعی برای [WebRTC](/en-US/docs/Glossary/WebRTC) به کار رود.

## مثال‌ها

### استفاده پایه

در این مثال، یک مدیریت‌کننده رویداد تنظیم شده است که با کلیک روی دکمه، محتویات یک عنصر رسانه با شناسه `"playback"` در یک {{domxref("MediaStream")}} ضبط می‌شود.
سپس می‌توان از این استریم برای اهداف دیگر استفاده کرد، مانند یک استریم WebRTC برای به اشتراک‌گذاری ویدیوهای از پیش ضبط‌شده با شخص دیگری در طول تماس ویدیویی.

```js
document.querySelector(".playAndRecord").addEventListener("click", () => {
  const playbackElement = document.getElementById("playback");
  const captureStream = playbackElement.captureStream();
  playbackElement.play();
});
```

برای یک مثال و توضیح طولانی‌تر و پیچیده‌تر، به [ضبط یک عنصر رسانه](/en-US/docs/Web/API/MediaStream_Recording_API/Recording_a_media_element) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ضبط یک عنصر رسانه](/en-US/docs/Web/API/MediaStream_Recording_API/Recording_a_media_element)
- [API ضبط MediaStream](/en-US/docs/Web/API/MediaStream_Recording_API)
- {{domxref("HTMLCanvasElement.captureStream()")}}
- {{domxref("MediaStream")}}
- [API WebRTC](/en-US/docs/Web/API/WebRTC_API)
