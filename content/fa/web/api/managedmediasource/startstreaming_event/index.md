---
title: "ManagedMediaSource: startstreaming event"
short-title: startstreaming
slug: Web/API/ManagedMediaSource/startstreaming_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.ManagedMediaSource.startstreaming_event
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}{{SeeCompatTable}}

رویداد **`startstreaming`** از واسط {{domxref("ManagedMediaSource")}} زمانی رخ می‌دهد که ویژگی {{domxref("ManagedMediaSource.streaming", "streaming")}} از `false` به `true` تغییر کند. این نشان می‌دهد که عامل کاربر (user agent) برای تضمین پخش بدون وقفه به داده‌های بیشتری نیاز دارد و برنامه باید واکشی و الحاق (append) قطعه‌های رسانه‌ای را آغاز کند.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("startstreaming", (event) => {});

onstartstreaming = (event) => {};
```

## Event type

یک {{domxref("Event")}} عمومی.

## Examples

### واکشی داده‌ها در پاسخ به startstreaming

در این مثال، یک {{domxref("ManagedMediaSource")}} ساخته می‌شود، به یک عنصر {{htmlelement("video")}} متصل می‌شود و از رویداد `startstreaming` برای شروع واکشی و الحاق داده‌های رسانه‌ای استفاده می‌شود.

```js
const videoUrl =
  "https://mdn.github.io/shared-assets/videos/flower-fragmented.mp4";
const mediaType = 'video/mp4; codecs="avc1.64001F, mp4a.40.2"';

if (ManagedMediaSource.isTypeSupported(mediaType)) {
  const video = document.createElement("video");
  const source = new ManagedMediaSource();

  video.controls = true;
  video.disableRemotePlayback = true;
  video.src = URL.createObjectURL(source);
  document.body.appendChild(video);

  source.addEventListener("sourceopen", () => {
    const sourceBuffer = source.addSourceBuffer(mediaType);

    source.addEventListener("startstreaming", async () => {
      console.log("startstreaming — fetching media data");
      const response = await fetch(videoUrl);
      const data = await response.arrayBuffer();
      sourceBuffer.appendBuffer(data);
    });
  });
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رویداد {{domxref("ManagedMediaSource.endstreaming_event", "endstreaming")}}
- {{domxref("ManagedMediaSource.streaming")}}
- {{domxref("ManagedMediaSource")}}
- {{domxref("MediaSource")}}