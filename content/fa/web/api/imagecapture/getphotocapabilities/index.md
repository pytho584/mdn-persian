---
title: "ImageCapture: getPhotoCapabilities() method"
short-title: getPhotoCapabilities()
slug: Web/API/ImageCapture/getPhotoCapabilities
page-type: web-api-instance-method
browser-compat: api.ImageCapture.getPhotoCapabilities
---

{{APIRef("Image Capture API")}}

متد **`getPhotoCapabilities()`** از رابط {{domxref("ImageCapture")}} یک {{jsxref("Promise")}} را برمی‌گرداند که با یک شیء حاوی محدوده‌های گزینه‌های پیکربندی موجود، حل می‌شود.

## نحو

```js-nolint
getPhotoCapabilities()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شیء حاوی ویژگی‌های زیر حل می‌شود:

- `redEyeReduction`
  - : یکی از مقادیر `"never"`، `"always"` یا `"controllable"` را برمی‌گرداند. مقدار `"controllable"` به این معنی است که کاهش قرمزی چشم دستگاه توسط کاربر قابل کنترل است.
- `imageHeight`
  - : یک شیء را برمی‌گرداند که محدوده ارتفاع تصویر پشتیبانی شده توسط عامل کاربر را نشان می‌دهد.
- `imageWidth`
  - : یک شیء را برمی‌گرداند که محدوده عرض تصویر پشتیبانی شده توسط عامل کاربر را نشان می‌دهد.
- `fillLightMode`
  - : یک آرایه از گزینه‌های نور پرکننده موجود را برمی‌گرداند. گزینه‌ها شامل `auto`، `off`، یا `flash` هستند.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر ویژگی `readyState` از `MediaStreamTrack` ارسال شده در سازنده `live` نباشد، پرتاب می‌شود.
- `OperationError` {{domxref("DOMException")}}
  - : اگر عملیات به هر دلیلی نتواند کامل شود، پرتاب می‌شود.

## مثال‌ها

مثال زیر، برگرفته از [نمونه Image Capture / Photo Resolution کروم](https://googlechrome.github.io/samples/image-capture/photo-resolution.html)، از نتایج `getPhotoCapabilities()` برای تغییر اندازه یک محدوده ورودی استفاده می‌کند. این مثال همچنین نشان می‌دهد که چگونه شیء {{domxref("ImageCapture")}} با استفاده از یک {{domxref("MediaStreamTrack")}} که از {{domxref("MediaStream")}} یک دستگاه گرفته شده، ایجاد می‌شود.

```js
const input = document.querySelector('input[type="range"]');

let imageCapture;

navigator.mediaDevices
  .getUserMedia({ video: true })
  .then((mediaStream) => {
    document.querySelector("video").srcObject = mediaStream;

    const track = mediaStream.getVideoTracks()[0];
    imageCapture = new ImageCapture(track);

    return imageCapture.getPhotoCapabilities();
  })
  .then((photoCapabilities) => {
    const settings = imageCapture.track.getSettings();

    input.min = photoCapabilities.imageWidth.min;
    input.max = photoCapabilities.imageWidth.max;
    input.step = photoCapabilities.imageWidth.step;

    return imageCapture.getPhotoSettings();
  })
  .then((photoSettings) => {
    input.value = photoSettings.imageWidth;
  })
  .catch((error) => console.error("آرغ!", error.name || error));
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}