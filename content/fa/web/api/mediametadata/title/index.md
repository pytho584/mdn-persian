---
title: "MediaMetadata: title property"
short-title: title
slug: Web/API/MediaMetadata/title
page-type: web-api-instance-property
browser-compat: api.MediaMetadata.title
---

{{APIRef("Media Session API")}}

ویژگی **`title`** در رابط {{domxref("MediaMetadata")}} عنوان رسانه‌ای را که قرار است پخش شود بازمی‌گرداند یا آن را تنظیم می‌کند.

## مقدار

یک {{jsxref("String")}} شامل عنوان رسانه.

## مثال‌ها

مثال زیر سازگاری مرورگر را بررسی می‌کند و فرادادهٔ جاری نشست رسانه را تنظیم می‌کند:

```js
if ("mediaSession" in navigator) {
  navigator.mediaSession.metadata = new MediaMetadata({
    title: "Unforgettable",
    artist: "Nat King Cole",
    album: "The Ultimate Collection (Remastered)",
    artwork: [
      {
        src: "https://dummyimage.com/96x96",
        sizes: "96x96",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/128x128",
        sizes: "128x128",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/192x192",
        sizes: "192x192",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/256x256",
        sizes: "256x256",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/384x384",
        sizes: "384x384",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/512x512",
        sizes: "512x512",
        type: "image/png",
      },
    ],
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}