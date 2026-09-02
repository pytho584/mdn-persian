---
title: "MediaSource: activeSourceBuffers property"
short-title: activeSourceBuffers
slug: Web/API/MediaSource/activeSourceBuffers
page-type: web-api-instance-property
browser-compat: api.MediaSource.activeSourceBuffers
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‌خواندنی **`activeSourceBuffers`** در رابط {{domxref("MediaSource")}} یک شیء {{domxref("SourceBufferList")}} برمی‌گرداند که شامل زیرمجموعه‌ای از اشیاء {{domxref("SourceBuffer")}} موجود در {{domxref("MediaSource.sourceBuffers", "sourceBuffers")}} است — فهرستی از اشیایی که مسیر ویدیویی انتخاب‌شده، مسیرهای صوتی فعال و مسیرهای متنی نمایش‌داده‌شده/مخفی را فراهم می‌کنند.

## مقدار

یک {{domxref("SourceBufferList")}} شامل اشیاء {{domxref("SourceBuffer")}} مربوط به هر یک از مسیرهای فعال.

## مثال‌ها

قطعه کد زیر بر اساس مثالی نوشته‌شده توسط Nick Desaulniers است ([مشاهده دموی کامل به صورت زنده](https://nickdesaulniers.github.io/netfix/demo/bufferAll.html)، یا [دانلود سورس](https://github.com/nickdesaulniers/netfix/blob/gh-pages/demo/bufferAll.html) برای بررسی بیشتر). تابع `getMediaSource()` که در اینجا تعریف نشده است، یک `MediaSource` برمی‌گرداند.

```js
const mediaSource = getMediaSource();

function sourceOpen() {
  console.log(mediaSource.readyState); // open
  const sourceBuffer = mediaSource.addSourceBuffer(mimeCodec);
  fetchAB(assetURL, (buf) => {
    sourceBuffer.addEventListener("updateend", () => {
      mediaSource.endOfStream();
      console.log(mediaSource.activeSourceBuffers);
      // شامل source buffer اضافه‌شده در بالا خواهد بود،
      // زیرا برای پخش در پخش‌کننده ویدیو انتخاب شده است.
      video.play();
      console.log(mediaSource.readyState); // ended
    });
    sourceBuffer.appendBuffer(buf);
  });
}

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SourceBuffer")}}
- {{domxref("SourceBufferList")}}