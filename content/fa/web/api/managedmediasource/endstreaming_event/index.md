---
title: "ManagedMediaSource: endstreaming event"
short-title: endstreaming
slug: Web/API/ManagedMediaSource/endstreaming_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.ManagedMediaSource.endstreaming_event
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}{{SeeCompatTable}}

رویداد **`endstreaming`** از رابط {{domxref("ManagedMediaSource")}} زمانی شلیک می‌شود که ویژگی {{domxref("ManagedMediaSource.streaming", "streaming")}} از `true` به `false` تغییر کند. این نشان می‌دهد که عامل کاربر (user agent) دادهٔ کافی را بافر کرده تا پخش بدون وقفه تضمین شود و برنامه می‌تواند دریافت سگمنت‌های رسانه‌ای جدید را متوقف کند.

## نحو

نام رویداد را در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید یا یک ویژگی مدیریت‌کنندهٔ رویداد تنظیم کنید.

```js-nolint
addEventListener("endstreaming", (event) => {});

onendstreaming = (event) => {};
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### توقف واکشی‌ها در واکنش به endstreaming

در این مثال یک {{domxref("ManagedMediaSource")}} ساخته می‌شود، به یک عنصر {{htmlelement("video")}} وصل می‌شود و از رویدادهای `startstreaming` و `endstreaming` برای کنترل زمان واکشی سگمنت‌های رسانه‌ای استفاده می‌شود.

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

  let shouldFetch = false;

  source.addEventListener("sourceopen", () => {
    const sourceBuffer = source.addSourceBuffer(mediaType);

    source.addEventListener("startstreaming", async () => {
      console.log("startstreaming — fetching media data");
      shouldFetch = true;
      const response = await fetch(videoUrl);
      const data = await response.arrayBuffer();
      if (shouldFetch) {
        sourceBuffer.appendBuffer(data);
      }
    });

    source.addEventListener("endstreaming", () => {
      console.log("endstreaming — enough data buffered");
      shouldFetch = false;
    });
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("ManagedMediaSource.startstreaming_event", "startstreaming")}}
- {{domxref("ManagedMediaSource.streaming")}}
- {{domxref("ManagedMediaSource")}}
- {{domxref("MediaSource")}}