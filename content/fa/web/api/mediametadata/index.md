---
title: MediaMetadata
slug: Web/API/MediaMetadata
page-type: web-api-interface
browser-compat: api.MediaMetadata
---

{{APIRef("Media Session API")}}

اینترفیس **`MediaMetadata`** متعلق به {{domxref("Media Session API", "", "", "nocode")}} به یک صفحهٔ وب اجازه میدهد فراداده‌های رسانه‌ای غنی را برای نمایش در رابط کاربری پلتفرم فراهم کند.

## سازنده

- {{domxref("MediaMetadata.MediaMetadata", "MediaMetadata()")}}
  - : یک شیء جدید `MediaMetaData` می‌سازد.

## ویژگی‌های نمونه

- {{domxref("MediaMetadata.album")}}
  - : نام آلبوم یا مجموعه‌ای که رسانهٔ در حال پخش در آن قرار دارد را برمی‌گرداند یا تنظیم می‌کند.
- {{domxref("MediaMetadata.artist")}}
  - : نام هنرمند، گروه، خالق و موارد مشابه برای رسانهٔ در حال پخش را برمی‌گرداند یا تنظیم می‌کند.
- {{domxref("MediaMetadata.artwork")}}
  - : آرایه‌ای از تصاویر مرتبط با رسانهٔ در حال پخش را برمی‌گرداند یا تنظیم می‌کند.
- {{domxref("MediaMetadata.chapterInfo")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : آرایه‌ای از اطلاعات فراداده‌ایِ فصل‌های مرتبط با رسانهٔ در حال پخش را برمی‌گرداند که با نمونه‌های شیء {{domxref("ChapterInformation")}} نمایش داده می‌شوند.
- {{domxref("MediaMetadata.title")}}
  - : عنوان رسانهٔ در حال پخش را برمی‌گرداند یا تنظیم می‌کند.

## مثال‌ها

مثال زیر سازگاری مرورگر را بررسی می‌کند و فراداده‌های فعلی نشست رسانه را تنظیم می‌کند.

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