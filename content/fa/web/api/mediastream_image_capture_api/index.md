---
title: MediaStream Image Capture API
slug: Web/API/MediaStream_Image_Capture_API
page-type: web-api-overview
browser-compat: api.ImageCapture
---

{{DefaultAPISidebar("Image Capture API")}}

**MediaStream Image Capture API** یک API برای گرفتن تصویر یا ویدیو از یک دستگاه عکاسی است. این API علاوه بر گرفتن داده، به شما امکان می‌دهد اطلاعاتی درباره قابلیت‌های دستگاه مانند اندازه تصویر، کاهش قرمزی چشم، وجود فلاش و مقادیر فعلی این تنظیمات را نیز بازیابی کنید. برعکس، این API امکان پیکربندی این قابلیت‌ها را در محدوده‌ای که دستگاه اجازه می‌دهد فراهم می‌کند.

## مفاهیم و کاربرد تصویربرداری MediaStream

فرآیند دریافت جریان تصویر یا ویدیو به شرح زیر انجام می‌شود. کد مثال از [نمونه‌های Image Capture کروم](https://googlechrome.github.io/samples/image-capture/) اقتباس شده است.

ابتدا با فراخوانی {{domxref("MediaDevices.getUserMedia()")}} به یک مرجع از دستگاه دسترسی پیدا کنید. مثال زیر می‌گوید هر دستگاه ویدیویی که در دسترس است را به من بده؛ اگرچه متد `getUserMedia()` امکان درخواست قابلیت‌های دقیق‌تری را نیز می‌دهد. این متد یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء {{domxref("MediaStream")}} حل می‌شود.

```js
navigator.mediaDevices.getUserMedia({ video: true }).then((mediaStream) => {
  // Do something with the stream.
});
```

در مرحله بعد، بخش تصویری جریان رسانه را جدا کنید. این کار را با فراخوانی {{domxref("MediaStream.getVideoTracks()")}} انجام دهید. این متد آرایه‌ای از اشیاء {{domxref("MediaStreamTrack")}} برمی‌گرداند. کد زیر فرض می‌کند که اولین آیتم در آرایه `MediaStreamTrack` همان موردی است که باید استفاده شود. می‌توانید از ویژگی‌های اشیاء `MediaStreamTrack` برای انتخاب مورد نیاز خود استفاده کنید.

```js
const track = mediaStream.getVideoTracks()[0];
```

در این مرحله، احتمالاً می‌خواهید قبل از گرفتن تصویر، قابلیت‌های دستگاه را پیکربندی کنید. می‌توانید این کار را با فراخوانی {{domxref("MediaStreamTrack.applyConstraints","applyConstraints()")}} روی شیء track و قبل از هر کار دیگری انجام دهید.

```js
let zoom = document.querySelector("#zoom");
const capabilities = track.getCapabilities();
// Check whether zoom is supported or not.
if (!capabilities.zoom) {
  return;
}
track.applyConstraints({ advanced: [{ zoom: zoom.value }] });
```

در نهایت، شیء `MediaStreamTrack` را به سازنده {{domxref("ImageCapture.ImageCapture()", "ImageCapture()")}} منتقل کنید. اگرچه یک `MediaStream` چند نوع track را نگه می‌دارد و روش‌های متعددی برای بازیابی آن‌ها ارائه می‌دهد، سازنده ImageCapture اگر {{domxref("MediaStreamTrack.kind")}} برابر با `"video"` نباشد، یک {{domxref("DOMException")}} از نوع `NotSupportedError` پرتاب می‌کند.

```js
let imageCapture = new ImageCapture(track);
```

## رابط‌ها

- {{domxref("ImageCapture")}}
  - : یک رابط برای گرفتن تصاویر از یک دستگاه عکاسی که از طریق یک {{domxref("MediaStreamTrack")}} معتبر ارجاع داده می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MediaStream")}}
- {{domxref("MediaStreamTrack")}}