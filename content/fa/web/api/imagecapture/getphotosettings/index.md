---
title: "ImageCapture: getPhotoSettings() method"
---

---
title: "ImageCapture: getPhotoSettings() method"
short-title: getPhotoSettings()
slug: Web/API/ImageCapture/getPhotoSettings
page-type: web-api-instance-method
browser-compat: api.ImageCapture.getPhotoSettings
---

{{APIRef("Image Capture API")}}

متد **`getPhotoSettings()`** در رابط {{domxref("ImageCapture")}} یک {{jsxref("Promise")}} برمی‌گرداند که با شیءای شامل تنظیمات فعلی پیکربندی عکس، resolve می‌شود.

## نحو

```js-nolint
getPhotoSettings()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با شیءای شامل ویژگی‌های زیر resolve می‌شود:

- `fillLightMode`
  - : تنظیم فلاش دستگاه ضبط؛ یکی از `"auto"`، `"off"` یا `"flash"`.
- `imageHeight`
  - : مقدار ارتفاع تصویر مورد نظر به‌صورت یک عدد صحیح. اگر مرورگر فقط از ارتفاع‌های گسسته پشتیبانی کند، نزدیک‌ترین مقدار عرض را به این تنظیم انتخاب می‌کند.
- `imageWidth`
  - : مقدار عرض تصویر مورد نظر به‌صورت یک عدد صحیح. اگر مرورگر فقط از عرض‌های گسسته پشتیبانی کند، نزدیک‌ترین مقدار عرض را به این تنظیم انتخاب می‌کند.
- `redEyeReduction`
  - : یک مقدار بولی که نشان می‌دهد آیا در صورت موجود بودن، کاهش قرمزی چشم (Red-Eye Reduction) باید استفاده شود یا خیر.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که ویژگی `readyState` از `MediaStreamTrack` ارسال‌شده در سازنده (constructor)، `live` نباشد.
- `OperationError` {{domxref("DOMException")}}
  - : اگر عملیات به هر دلیلی نتواند تکمیل شود، پرتاب می‌شود.

## مثال‌ها

مثال زیر، که از [Chrome's Image Capture / Photo Resolution Sample](https://googlechrome.github.io/samples/image-capture/photo-resolution.html) استخراج شده، از نتایج `getPhotoSettings()` برای تغییر اندازه یک محدوده ورودی (input range) استفاده می‌کند. این مثال همچنین نشان می‌دهد که چگونه شیء {{domxref("ImageCapture")}} با استفاده از یک {{domxref("MediaStreamTrack")}} که از {{domxref("MediaStream")}} یک دستگاه به دست آمده، ساخته می‌شود.

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
  .catch((error) => console.error("Argh!", error.name || error));
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}