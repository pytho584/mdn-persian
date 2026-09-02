---
title: "ImageCapture"
slug: Web/API/ImageCapture
page-type: web-api-interface
browser-compat: api.ImageCapture
---

{{APIRef("Image Capture API")}}

رابط **`ImageCapture`** از [MediaStream Image Capture API](/en-US/docs/Web/API/MediaStream_Image_Capture_API) روش‌هایی را برای گرفتن تصاویر یا عکس‌ها از یک دوربین یا سایر دستگاه‌های عکاسی فراهم می‌کند. این رابط یک واسط برای گرفتن تصاویر از یک دستگاه عکاسی که از طریق یک {{domxref("MediaStreamTrack")}} معتبر ارجاع داده شده است، ارائه می‌دهد.

## سازنده

- {{domxref("ImageCapture.ImageCapture()", "ImageCapture()")}}
  - : یک شیء `ImageCapture` جدید ایجاد می‌کند که می‌تواند برای گرفتن فریم‌های ثابت (عکس) از یک {{domxref("MediaStreamTrack")}} داده شده که یک جریان ویدیویی را نشان می‌دهد، استفاده شود.

## ویژگی‌های نمونه

- {{domxref("ImageCapture.track")}} {{ReadOnlyInline}}
  - : یک ارجاع به {{domxref("MediaStreamTrack")}} ارسال شده به سازنده را برمی‌گرداند.

## روش‌های نمونه

- {{domxref("ImageCapture.takePhoto()")}}
  - : یک نوردهی واحد با استفاده از دستگاه ضبط ویدیو که یک {{domxref("MediaStreamTrack")}} را تأمین می‌کند، می‌گیرد و یک {{jsxref("Promise")}} برمی‌گرداند که با یک {{domxref("Blob")}} حاوی داده‌ها حل می‌شود.
- {{domxref("ImageCapture.getPhotoCapabilities()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء حاوی محدوده‌های گزینه‌های پیکربندی موجود حل می‌شود.
- {{domxref("ImageCapture.getPhotoSettings()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء حاوی تنظیمات پیکربندی فعلی عکس حل می‌شود.
- {{domxref("ImageCapture.grabFrame()")}}
  - : یک عکس فوری از ویدیوی زنده در یک {{domxref("MediaStreamTrack")}} می‌گیرد و در صورت موفقیت، یک {{domxref("ImageBitmap")}} برمی‌گرداند.

## مثال

کد زیر از [نمونه Grab Frame - Take Photo کروم](https://googlechrome.github.io/samples/image-capture/grab-frame-take-photo.html) گرفته شده است. از آنجایی که `ImageCapture` به مکانی برای گرفتن تصویر نیاز دارد، مثال زیر با یک دستگاه رسانه‌ای (یعنی یک دوربین) شروع می‌شود.

این مثال تقریباً نشان می‌دهد که چگونه یک {{domxref("MediaStreamTrack")}} از یک {{domxref("MediaStream")}} دستگاه استخراج می‌شود. سپس از این track برای ایجاد یک شیء `ImageCapture` استفاده می‌شود تا بتوان `takePhoto()` و `grabFrame()` را فراخوانی کرد. در نهایت، نحوه اعمال نتایج این فراخوانی‌ها به یک شیء canvas نشان داده می‌شود.

```js
let imageCapture;

function onGetUserMediaButtonClick() {
  navigator.mediaDevices
    .getUserMedia({ video: true })
    .then((mediaStream) => {
      document.querySelector("video").srcObject = mediaStream;

      const track = mediaStream.getVideoTracks()[0];
      imageCapture = new ImageCapture(track);
    })
    .catch((error) => console.error(error));
}

function onGrabFrameButtonClick() {
  imageCapture
    .grabFrame()
    .then((imageBitmap) => {
      const canvas = document.querySelector("#grabFrameCanvas");
      drawCanvas(canvas, imageBitmap);
    })
    .catch((error) => console.error(error));
}

function onTakePhotoButtonClick() {
  imageCapture
    .takePhoto()
    .then((blob) => createImageBitmap(blob))
    .then((imageBitmap) => {
      const canvas = document.querySelector("#takePhotoCanvas");
      drawCanvas(canvas, imageBitmap);
    })
    .catch((error) => console.error(error));
}

/* Utils */

function drawCanvas(canvas, img) {
  canvas.width = getComputedStyle(canvas).width.split("px")[0];
  canvas.height = getComputedStyle(canvas).height.split("px")[0];
  let ratio = Math.min(canvas.width / img.width, canvas.height / img.height);
  let x = (canvas.width - img.width * ratio) / 2;
  let y = (canvas.height - img.height * ratio) / 2;
  canvas.getContext("2d").clearRect(0, 0, canvas.width, canvas.height);
  canvas
    .getContext("2d")
    .drawImage(
      img,
      0,
      0,
      img.width,
      img.height,
      x,
      y,
      img.width * ratio,
      img.height * ratio,
    );
}

document.querySelector("video").addEventListener("play", () => {
  document.querySelector("#grabFrameButton").disabled = false;
  document.querySelector("#takePhotoButton").disabled = false;
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}