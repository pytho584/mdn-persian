---
title: ChapterInformation
slug: Web/API/ChapterInformation
page-type: web-api-interface
status:
  - experimental
browser-compat: api.ChapterInformation
---

{{APIRef("Media Session API")}}{{SeeCompatTable}}

**`ChapterInformation`** 接口 از {{domxref("Media Session API", "", "", "nocode")}} ابرداده‌های مربوط به یک فصل خاص از یک منبع رسانه‌ای (یعنی یک فایل ویدئویی یا صوتی) را نمایش می‌دهد.

اطلاعات فصل برای یک منبع رسانه‌ای مشخص، هنگام ایجاد اولیه آن، از طریق ویژگی `chapterInfo` در شیء مقداردهی اولیه سازنده {{domxref("MediaMetadata.MediaMetadata", "MediaMetadata()")}} تنظیم می‌شود. این ویژگی یک آرایه از اشیاء `ChapterInformation` را به عنوان مقدار خود می‌گیرد.

شما می‌توانید اطلاعات فصل را برای یک شیء {{domxref("MediaMetadata")}} موجود از طریق ویژگی {{domxref("MediaMetadata.chapterInfo", "chapterInfo")}} آن دسترسی داشته باشید. این ویژگی یک آرایه از اشیاء `ChapterInformation` برمی‌گرداند.

## ویژگی‌های نمونه

- {{domxref("ChapterInformation.artwork")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک {{jsxref("Array")}} از اشیاء مرتبط با تصاویر فصل را برمی‌گرداند.
- {{domxref("ChapterInformation.startTime")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک عدد بر حسب ثانیه را برمی‌گرداند که زمان شروع فصل را نشان می‌دهد.
- {{domxref("ChapterInformation.title")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک رشته (string) را برمی‌گرداند که عنوان فصل را نشان می‌دهد.

## مثال‌ها

کد نمونه زیر از [نمونه ویدیو / رسانه (Video / Media Session Sample)](https://googlechrome.github.io/samples/media-session/video.html) ساختار معمولی برای شیء `ChapterInformation` را نشان می‌دهد:

```js
const BASE_URL = "https://storage.googleapis.com/media-session/";

const metadata = {
  // …
  chapterInfo: [
    {
      title: "Chapter 1",
      startTime: 0,
      artwork: [
        {
          src: `${BASE_URL}sintel/chapter1-128.png`,
          sizes: "128x128",
          type: "image/png",
        },
        {
          src: `${BASE_URL}sintel/chapter1-512.png`,
          sizes: "512x512",
          type: "image/png",
        },
      ],
    },
    {
      title: "Chapter 2",
      startTime: 37,
      artwork: [
        {
          src: `${BASE_URL}sintel/chapter2-128.png`,
          sizes: "128x128",
          type: "image/png",
        },
        {
          src: `${BASE_URL}sintel/chapter2-512.png`,
          sizes: "512x512",
          type: "image/png",
        },
      ],
    },
  ],
};
```

قطعه کد زیر نحوه استفاده از آن را در کد Media Session نشان می‌دهد (ویژگی شیء فوق بخشی از شیء `playlist` است که در زیر به آن اشاره شده است):

```js
function updateMetadata() {
  const track = playlist[index];

  log(`Playing ${track.title} track...`);
  navigator.mediaSession.metadata = new MediaMetadata({
    title: track.title,
    artist: track.artist,
    artwork: track.artwork,
    chapterInfo: track.chapterInfo,
  });

  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MediaMetadata")}}