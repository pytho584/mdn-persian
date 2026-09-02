---
title: "ImageCapture: ImageCapture() constructor"
short-title: ImageCapture()
slug: Web/API/ImageCapture/ImageCapture
page-type: web-api-constructor
browser-compat: api.ImageCapture.ImageCapture
---

{{APIRef("Image Capture API")}}

سازنده **`ImageCapture()`** یک شیء جدید از نوع {{domxref("ImageCapture")}} ایجاد می‌کند.

## نحو (Syntax)

```js-nolint
new ImageCapture(videoTrack)
```

### پارامترها

- `videoTrack`
  - : یک {{domxref("MediaStreamTrack")}} که تصاویر ثابت از آن گرفته می‌شود. این می‌تواند هر منبعی باشد، مانند یک جریان ورودی از یک کنفرانس ویدیویی، یک فیلم در حال پخش، یا جریان یک وبکم.

### مقدار بازگشتی

یک شیء جدید `ImageCapture` که می‌توان از آن برای گرفتن فریم‌های ثابت از ردیف ویدیویی مشخص شده استفاده کرد.

### استثناها (Exceptions)

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر خاصیت `kind` پارامتر `videoTrack` برابر با `video` نباشد، این خطا پرتاب می‌شود.

## مثال‌ها

مثال زیر نحوه استفاده از فراخوانی {{domxref("MediaDevices.getUserMedia()")}} را برای دریافت {{domxref("MediaStreamTrack")}} مورد نیاز سازنده `ImageCapture()` نشان می‌دهد.

```js
navigator.mediaDevices
  .getUserMedia({ video: true })
  .then((mediaStream) => {
    document.querySelector("video").srcObject = mediaStream;
    const track = mediaStream.getVideoTracks()[0];
    imageCapture = new ImageCapture(track);
  })
  .catch((error) => console.error(error));
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}