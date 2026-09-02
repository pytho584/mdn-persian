---
title: ImageDecoder
slug: Web/API/ImageDecoder
page-type: web-api-interface
browser-compat: api.ImageDecoder
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

رابط **`ImageDecoder`** از {{domxref('WebCodecs API','','','true')}} روشی برای باز کردن بسته‌بندی و رمزگشایی داده‌های تصویری رمزگذاری‌شده فراهم می‌کند.

## سازنده

- {{domxref("ImageDecoder.ImageDecoder", "ImageDecoder()")}}
  - : یک شیء جدید `ImageDecoder` ایجاد می‌کند.

## ویژگی‌های نمونه

- {{domxref("ImageDecoder.complete")}} {{ReadOnlyInline}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا داده‌های رمزگذاری‌شده به طور کامل بافر شده‌اند یا خیر.
- {{domxref("ImageDecoder.completed")}} {{ReadOnlyInline}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که به محض `true` شدن `complete` حل می‌شود.
- {{domxref("ImageDecoder.tracks")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("ImageTrackList")}} برمی‌گرداند که شامل لیست مسیرهای موجود و روشی برای انتخاب یک مسیر جهت رمزگشایی است.
- {{domxref("ImageDecoder.type")}} {{ReadOnlyInline}}
  - : یک رشته برمی‌گرداند که نشان‌دهنده [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) تنظیم‌شده در زمان ساخت است.

## روش‌های ایستا

- {{domxref("ImageDecoder.isTypeSupported_static", "ImageDecoder.isTypeSupported()")}}
  - : نشان می‌دهد که آیا [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) داده‌شده برای باز کردن بسته‌بندی و رمزگشایی پشتیبانی می‌شود یا خیر.

## روش‌های نمونه

- {{domxref("ImageDecoder.close()")}}
  - : تمام کارهای در انتظار را پایان می‌دهد و منابع سیستم را آزاد می‌کند.
- {{domxref("ImageDecoder.decode()")}}
  - : یک پیام کنترل برای رمزگشایی فریم یک تصویر در صف قرار می‌دهد.
- {{domxref("ImageDecoder.reset()")}}
  - : تمام عملیات‌های در انتظار `decode()` را لغو می‌کند.

## مثال‌ها

با توجه به یک عنصر {{HTMLElement("canvas")}}:

```html
<canvas></canvas>
```

کد زیر یک تصویر متحرک را رمزگشایی کرده و روی آن بوم (canvas) نمایش می‌دهد:

```js
let imageDecoder = null;
let imageIndex = 0;

function renderImage(result) {
  const canvas = document.querySelector("canvas");
  const canvasContext = canvas.getContext("2d");

  canvasContext.drawImage(result.image, 0, 0);

  const track = imageDecoder.tracks.selectedTrack;

  // We check complete here since `frameCount` won't be stable until all
  // data has been received. This may cause us to receive a RangeError
  // during the decode() call below which needs to be handled.
  if (imageDecoder.complete) {
    if (track.frameCount === 1) return;

    if (imageIndex + 1 >= track.frameCount) imageIndex = 0;
  }

  // Decode the next frame ahead of display so it's ready in time.
  imageDecoder
    .decode({ frameIndex: ++imageIndex })
    .then((nextResult) =>
      setTimeout(() => {
        renderImage(nextResult);
      }, result.image.duration / 1000.0),
    )
    .catch((e) => {
      // We can end up requesting an imageIndex past the end since
      // we're using a ReadableStream from fetch(), when this happens
      // just wrap around.
      if (e instanceof RangeError) {
        imageIndex = 0;
        imageDecoder.decode({ frameIndex: imageIndex }).then(renderImage);
      } else {
        throw e;
      }
    });
}

function decodeImage(imageByteStream) {
  imageDecoder = new ImageDecoder({ data: imageByteStream, type: "image/gif" });
  imageDecoder.decode({ frameIndex: imageIndex }).then(renderImage);
}

fetch("fancy.gif").then((response) => decodeImage(response.body));
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}