---
title: "MediaStream: getVideoTracks() method"
short-title: getVideoTracks()
slug: Web/API/MediaStream/getVideoTracks
page-type: web-api-instance-method
browser-compat: api.MediaStream.getVideoTracks
---

{{APIRef("Media Capture and Streams")}}

متد **`getVideoTracks()`** در رابط {{domxref("MediaStream")}} دنباله‌ای از شیءهای {{domxref("MediaStreamTrack")}} را برمی‌گرداند که نشان‌دهندهٔ ترک‌های ویدیویی این استریم هستند.

## سینتکس

```js-nolint
getVideoTracks()
```

### پارامترها

هیچ.

### مقدار برگشتی

آرایه‌ای از شیءهای {{domxref("MediaStreamTrack")}}، یکی برای هر ترک ویدیویی موجود در استریم رسانه‌ای. ترک‌های ویدیویی، ترک‌هایی هستند که ویژگی {{domxref("MediaStreamTrack.kind", "kind")}} آن‌ها `video` است. اگر استریم هیچ ترک ویدیویی نداشته باشد، آرایه خالی است.

> [!NOTE]
> ترتیب ترک‌ها در مشخصات فنی تعریف نشده است و ممکن است در فراخوانی‌های مختلف `getVideoTracks()` یکسان نباشد.

## مثال‌ها

مثال زیر، برگرفته از [نمونهٔ Chrome با عنوان Image Capture / Photo Resolution](https://googlechrome.github.io/samples/image-capture/photo-resolution.html)، از `getVideoTracks()` برای دریافت یک ترک و ارسال آن به سازندهٔ {{domxref("ImageCapture.ImageCapture", "ImageCapture()")}} استفاده می‌کند.

```js
let imageCapture;

navigator.mediaDevices.getUserMedia({ video: true }).then((mediaStream) => {
  document.querySelector("video").srcObject = mediaStream;

  const track = mediaStream.getVideoTracks()[0];
  imageCapture = new ImageCapture(track);

  return imageCapture.getPhotoCapabilities();
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}