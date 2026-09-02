---
title: "MediaSource: MediaSource() constructor"
short-title: MediaSource()
slug: Web/API/MediaSource/MediaSource
page-type: web-api-constructor
browser-compat: api.MediaSource.MediaSource
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

سازندهٔ **`MediaSource()`** از رابط {{domxref("MediaSource")}} یک شیء `MediaSource` جدید ساخته و بازمی‌گرداند که هیچ بافر منبع (source buffer) مرتبطی ندارد.

## سینتکس

```js-nolint
new MediaSource()
```

### پارامترها

هیچ.

## مثال‌ها

قطعه کد زیر از نمونه‌ای نوشته‌شده توسط Nick Desaulniers گرفته شده است ([مشاهدهٔ دموی کامل به‌صورت زنده](https://nickdesaulniers.github.io/netfix/demo/bufferAll.html) یا [دانلود کد منبع](https://github.com/nickdesaulniers/netfix/blob/gh-pages/demo/bufferAll.html) برای بررسی بیشتر).

```js
const video = document.querySelector("video");

const assetURL = "frag_bunny.mp4";
// Need to be specific for Blink regarding codecs
// ./mp4info frag_bunny.mp4 | grep Codec
const mimeCodec = 'video/mp4; codecs="avc1.42E01E, mp4a.40.2"';

if ("MediaSource" in window && MediaSource.isTypeSupported(mimeCodec)) {
  const mediaSource = new MediaSource();
  // console.log(mediaSource.readyState); // closed
  video.src = URL.createObjectURL(mediaSource);
  mediaSource.addEventListener("sourceopen", sourceOpen);
} else {
  console.error("Unsupported MIME type or codec: ", mimeCodec);
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