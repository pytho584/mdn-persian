---
title: "MediaMetadata: MediaMetadata() constructor"
short-title: MediaMetadata()
slug: Web/API/MediaMetadata/MediaMetadata
page-type: web-api-constructor
browser-compat: api.MediaMetadata.MediaMetadata
---

{{APIRef("Media Session API")}}

سازندهٔ **`MediaMetadata()`** یک شیء جدید از نوع {{domxref("MediaMetadata")}} می‌سازد.

## Syntax

```js-nolint
new MediaMetadata()
new MediaMetadata(metadata)
```

### پارامترها

- `metadata` {{optional_inline}}
  - : پارامترهای فراداده به صورت زیر هستند:
    - `album` {{optional_inline}}
      - : نام آلبوم یا مجموعه‌ای که رسانهٔ در حال پخش به آن تعلق دارد. مقدار پیش‌فرض آن رشتهٔ خالی (`""`) است.
    - `artist` {{optional_inline}}
      - : نام هنرمند، گروه یا پدیدآورندهٔ رسانهٔ در حال پخش. مقدار پیش‌فرض آن رشتهٔ خالی (`""`) است.
    - `artwork` {{optional_inline}}
      - : یک {{jsxref("Array")}} از اشیایی که تصاویر مرتبط با رسانهٔ در حال پخش را نشان می‌دهند؛ مقدار پیش‌فرض آن یک آرایهٔ خالی است. ساختار شیء به صورت زیر است:
        - `src`
          - : نشانی اینترنتی (URL) که عامل کاربر (user agent) داده‌های تصویر را از آن دریافت می‌کند.
        - `sizes` {{optional_inline}}
          - : منبع را در چند اندازه مشخص می‌کند تا عامل کاربر مجبور نباشد یک تصویر را مقیاس‌دهی کند. مقدار پیش‌فرض آن رشتهٔ خالی (`""`) است.
        - `type` {{optional_inline}}
          - : راهنمای {{Glossary("MIME type")}} برای عامل کاربر است که به آن امکان می‌دهد تصاویری از انواع ناپشتیبانی‌شده را نادیده بگیرد. با این حال، عامل کاربر ممکن است پس از دانلود تصویر، همچنان از تشخیص نوع MIME برای تعیین نوع آن استفاده کند. مقدار پیش‌فرض آن رشتهٔ خالی (`""`) است.
    - `chapterInfo` {{optional_inline}}
      - : آرایه‌ای از نمونه‌های شیء {{domxref("ChapterInformation")}} که فرادادهٔ اطلاعات فصل مرتبط با رسانه را نشان می‌دهد. ساختار شیء به صورت زیر است:
        - `artwork` {{optional_inline}}
          - : یک {{jsxref("Array")}} از اشیاء `artwork` (به بالا مراجعه کنید) که تصاویر مرتبط با فصل را نشان می‌دهد. اگر حذف شود، `artwork` به یک آرایهٔ خالی پیش‌فرض می‌شود.
        - `startTime` {{optional_inline}}
          - : عددی که زمان شروع فصل را بر حسب ثانیه نشان می‌دهد. اگر حذف شود، `startTime` به `0` پیش‌فرض می‌شود.
        - `title` {{optional_inline}}
          - : رشته‌ای که عنوان فصل را نشان می‌دهد. اگر حذف شود، `title` به رشتهٔ خالی (`""`) پیش‌فرض می‌شود.
    - `title` {{optional_inline}}
      - : عنوان رسانه‌ای که قرار است پخش شود. مقدار پیش‌فرض آن رشتهٔ خالی (`""`) است.

## مثال

مثال زیر یک شیء جدید {{domxref("MediaMetadata")}} را با استفاده از قالب صحیح فراداده می‌سازد.

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