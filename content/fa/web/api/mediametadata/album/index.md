---
title: "MediaMetadata: album property"
short-title: album
slug: Web/API/MediaMetadata/album
page-type: web-api-instance-property
browser-compat: api.MediaMetadata.album
---

{{APIRef("Media Session API")}}

ویژگی **`album`** در رابط {{domxref("MediaMetadata")}} نام آلبوم یا مجموعه‌ای را که رسانهٔ در حال پخش به آن تعلق دارد، برمی‌گرداند یا تنظیم می‌کند.

## مقدار

یک {{jsxref("String")}} شامل نام آلبوم.

## مثال‌ها

مثال زیر سازگاری مرورگر را بررسی می‌کند و فراداده‌های جلسهٔ رسانه را تنظیم می‌کند.

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