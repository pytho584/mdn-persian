---
title: "MediaMetadata: artwork property"
short-title: artwork
slug: Web/API/MediaMetadata/artwork
page-type: web-api-instance-property
browser-compat: api.MediaMetadata.artwork
---

{{APIRef("Media Session API")}}

ویژگی **`artwork`** در رابط {{domxref("MediaMetadata")}}، آرایه‌ای از اشیا را برمی‌گرداند یا تنظیم می‌کند که تصاویر مرتبط با رسانهٔ در حال پخش را نشان می‌دهند.

## مقدار

یک {{jsxref("Array")}} از اشیا، که هر کدام شامل فیلدهای زیر است:

- `src`
  - : نشانی اینترنتی (URL) که عامل کاربر (user agent) داده‌های تصویر را از آن دریافت می‌کند.
- `sizes` {{optional_inline}}
  - : منبع را در چند اندازه مشخص می‌کند تا عامل کاربر مجبور نباشد یک تصویر را تغییر اندازه دهد. مقدار پیش‌فرض آن رشتهٔ خالی (`""`) است.
- `type` {{optional_inline}}
  - : راهنمای {{Glossary("MIME type")}} برای عامل کاربر است و به آن اجازه می‌دهد تصاویری از نوع‌هایی را که پشتیبانی نمی‌کند نادیده بگیرد. با این حال، عامل کاربر ممکن است پس از بارگیری تصویر، همچنان برای تعیین نوع آن از تشخیص نوع MIME (MIME type sniffing) استفاده کند. مقدار پیش‌فرض آن رشتهٔ خالی (`""`) است.

## مثال‌ها

مثال زیر سازگاری مرورگر را بررسی می‌کند و فرادادهٔ فعلی نشست رسانه‌ای (media session) را تنظیم می‌کند.

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