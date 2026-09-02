---
title: "MediaSource: sourceopen event"
short-title: sourceopen
slug: Web/API/MediaSource/sourceopen_event
page-type: web-api-event
browser-compat: api.MediaSource.sourceopen_event
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

رویداد **`sourceopen`** زمانی رخ می‌دهد که {{domxref("MediaSource.readyState", "readyState")}} یک شیء {{domxref("MediaSource")}} به `"open"` تغییر کند. این نشان می‌دهد که `MediaSource` آماده دریافت داده از اشیاء {{domxref("SourceBuffer")}} است. این رویداد می‌تواند یا زمانی رخ دهد که شیء `MediaSource` برای اولین بار به یک عنصر رسانه‌ای متصل می‌شود، یا زمانی که {{domxref("MediaSource.readyState", "readyState")}} از `"ended"` به `"open"` بازمی‌گردد.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js
addEventListener("sourceopen", (event) => {});

onsourceopen = (event) => {};
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### مدیریت رویداد sourceopen

این مثال یک {{domxref("MediaSource")}} راه‌اندازی می‌کند، آن را به یک عنصر ویدیو متصل می‌کند و به رویداد `sourceopen` گوش می‌دهد. وقتی رویداد فعال می‌شود، یک {{domxref("SourceBuffer")}} برای مدیریت داده ویدیو اضافه می‌کند، داده را دریافت می‌کند، آن را به بافر اضافه می‌کند و در نهایت وقتی منبع (source) به پایان می‌رسد، URL شیء را لغو می‌کند.

```js
const video = document.getElementById("myVideo");
const mediaSource = new MediaSource();

video.src = URL.createObjectURL(mediaSource);

mediaSource.addEventListener("sourceopen", (event) => {
  console.log("MediaSource sourceopen:", event);
  // Add source buffers and begin adding media data.
  const sourceBuffer = mediaSource.addSourceBuffer(
    'video/mp4; codecs="avc1.42E01E"',
  );
  fetch("video-data.mp4")
    .then((response) => response.arrayBuffer())
    .then((data) => {
      sourceBuffer.appendBuffer(data);
    });
});

mediaSource.addEventListener("sourceended", () => {
  URL.revokeObjectURL(video.src);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}