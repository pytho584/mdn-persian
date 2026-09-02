---
title: "MediaSource: sourceended event"
short-title: sourceended
slug: Web/API/MediaSource/sourceended_event
page-type: web-api-event
browser-compat: api.MediaSource.sourceended_event
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

رویداد **`sourceended`** زمانی پرتاب می‌شود که {{domxref("MediaSource.readyState", "readyState")}} یک شیء {{domxref("MediaSource")}} به `"ended"` تغییر کند. این نشان می‌دهد که برنامه ارسال داده به `MediaSource` را به پایان رسانده است. وقتی یک برنامه، افزودن تمام داده‌های رسانه‌ای به شیءهای {{domxref("SourceBuffer")}} مرتبط با یک `MediaSource` را تمام کند، متد {{domxref("MediaSource.endOfStream()")}} را روی آن `MediaSource` فراخوانی می‌کند. این کار باعث می‌شود {{domxref("MediaSource.readyState", "readyState")}} به `"ended"` تغییر کند و رویداد `sourceended` فعال شود.

## Syntax

برای استفاده، نام رویداد را در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی handler رویداد تنظیم کنید.

```js-nolint
addEventListener("sourceended", (event) => {})

onsourceended = (event) => {}
```

## Event type

یک {{domxref("Event")}} عمومی.

## Examples

### مدیریت رویداد sourceopen

این مثال، راه‌اندازی یک عنصر ویدیو برای پخش و مدیریت رویداد `sourceended` را برای مدیریت صحیح منابع نشان می‌دهد. کد یک {{domxref("MediaSource")}} تنظیم می‌کند، با واکشی و بافر کردن داده ویدیو پخش را آغاز می‌کند و سپس از رویداد `sourceended` برای انجام کارهای پاک‌سازی مانند حذف event listenerها و اطلاع‌رسانی به کاربر هنگام پایان پخش استفاده می‌کند.

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
      sourceBuffer.addEventListener("updateend", () => {
        mediaSource.endOfStream();
      });
    });
});

mediaSource.addEventListener("sourceended", (event) => {
  console.log("MediaSource sourceended:", event);
  URL.revokeObjectURL(video.src);
  // Perform cleanup

  // Remove event listeners from SourceBuffer and MediaSource
  sourceBuffer.removeEventListener("updateend", () => {});
  mediaSource.removeEventListener("sourceopen", () => {});

  // Notify user (e.g., display a "Playback finished" message)
  const messageElement = document.createElement("p");
  messageElement.textContent = "Playback finished.";
  document.body.appendChild(messageElement);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("MediaSource.endOfStream()")}}