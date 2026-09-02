---
title: "ImageCapture: grabFrame() method"
short-title: grabFrame()
slug: Web/API/ImageCapture/grabFrame
page-type: web-api-instance-method
browser-compat: api.ImageCapture.grabFrame
---

{{APIRef("Image Capture API")}}

**`grabFrame()`** متدی از رابط {{domxref("ImageCapture")}} است که یک عکس فوری از ویدیوی زنده در یک {{domxref("MediaStreamTrack")}} می‌گیرد و یک {{jsxref("Promise")}} برمی‌گرداند که با یک {{domxref("ImageBitmap")}} حاوی آن عکس فوری resolve می‌شود.

## نحو

```js-nolint
grabFrame()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شیء {{domxref("ImageBitmap")}} resolve می‌شود.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر ویژگی `readyState` شیء `MediaStreamTrack` ارسال‌شده به سازنده، برابر `live` نباشد، این خطا پرتاب می‌شود.
- `UnknownError` {{domxref("DOMException")}}
  - : اگر عملیات به هر دلیلی نتواند کامل شود، پرتاب می‌شود.

## مثال‌ها

این مثال از این [دموی Simple Image Capture](https://simpl.info/imagecapture/) برگرفته شده است. نشان می‌دهد که چگونه از {{jsxref("Promise")}} برگشتی `grabFrame()` برای کپی کردن فریم برگشتی در یک عنصر {{htmlelement("canvas")}} استفاده کنید. برای سادگی، نحوه نمونه‌سازی شیء {{domxref("ImageCapture")}} در آن نشان داده نشده است.

```js
let grabFrameButton = document.querySelector("button#grabFrame");
let canvas = document.querySelector("canvas");

grabFrameButton.onclick = grabFrame;

function grabFrame() {
  imageCapture
    .grabFrame()
    .then((imageBitmap) => {
      console.log("Grabbed frame:", imageBitmap);
      canvas.width = imageBitmap.width;
      canvas.height = imageBitmap.height;
      canvas.getContext("2d").drawImage(imageBitmap, 0, 0);
      canvas.classList.remove("hidden");
    })
    .catch((error) => {
      console.error("grabFrame() error: ", error);
    });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}