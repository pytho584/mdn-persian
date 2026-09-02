---
title: "MediaSource: sourceclose event"
short-title: sourceclose
slug: Web/API/MediaSource/sourceclose_event
page-type: web-api-event
browser-compat: api.MediaSource.sourceclose_event
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

رویداد **`sourceclose`** زمانی شلیک می‌شود که {{domxref("MediaSource.readyState", "readyState")}} یک شیء {{domxref("MediaSource")}} به `"closed"` تغییر کند. این نشان می‌دهد که `MediaSource` از عنصر رسانه جدا شده است.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("sourceclose", (event) => { })

onsourceclose = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### مدیریت رویداد sourceclose

این مثال جدا کردن یک عنصر رسانه از یک `MediaSource` و مدیریت رویداد `sourceclose` برای مدیریت صحیح منابع را نشان می‌دهد. کد یک {{domxref("MediaSource")}} تنظیم می‌کند، آن را به یک عنصر ویدیو متصل می‌کند و به رویداد `sourceclose` گوش می‌دهد. هنگامی که رویداد شلیک می‌شود، کارهای پاک‌سازی (`revokeObjectURL`) را انجام می‌دهد.

```js
const video = document.getElementById("myVideo");
const mediaSource = new MediaSource();

video.src = URL.createObjectURL(mediaSource);

mediaSource.addEventListener("sourceopen", (event) => {
  const sourceBuffer = mediaSource.addSourceBuffer(
    'video/mp4; codecs="avc1.42E01E"',
  );
  fetch("video-data.mp4")
    .then((response) => response.arrayBuffer())
    .then((data) => {
      sourceBuffer.appendBuffer(data);
    });
});

function detachMediaSource() {
  video.src = null; // Detach the MediaSource
}

mediaSource.addEventListener("sourceclose", (event) => {
  console.log("MediaSource sourceclose:", event);
  // Perform cleanup tasks here, e.g., release resources, update UI
  URL.revokeObjectURL(video.src); // Clean up the object URL
});

// Call detachMediaSource() when appropriate, e.g., on a button click
document
  .getElementById("detachButton")
  .addEventListener("click", detachMediaSource);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}