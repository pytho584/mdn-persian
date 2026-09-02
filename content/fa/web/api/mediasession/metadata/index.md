---
title: "MediaSession: metadata property"
short-title: metadata
slug: Web/API/MediaSession/metadata
page-type: web-api-instance-property
browser-compat: api.MediaSession.metadata
---

{{APIRef("Media Session API")}}

ویژگی **`metadata`** در رابط {{domxref("MediaSession")}} شامل یک شیء {{domxref("MediaMetadata")}} است که اطلاعات توصیفی دربارهٔ رسانهٔ در حال پخش را فراهم می‌کند، یا اگر فراداده تنظیم نشده باشد، مقدار `null` دارد. این فراداده توسط مرورگر به دستگاه ارسال می‌شود تا در هر رابط کاربری استاندارد کنترل رسانه که دستگاه ارائه می‌دهد نمایش داده شود.

## مقدار

یک نمونه از {{domxref("MediaMetadata")}} که حاوی اطلاعات مربوط به رسانهٔ در حال پخش است.

## مثال

مثال زیر بررسی سازگاری می‌کند و یک نشست رسانه‌ای جدید با فرادادهٔ مرتبط ایجاد می‌نماید:

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