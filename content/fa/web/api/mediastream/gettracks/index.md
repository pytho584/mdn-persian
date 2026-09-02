---
title: "MediaStream: getTracks() method"
short-title: getTracks()
slug: Web/API/MediaStream/getTracks
page-type: web-api-instance-method
browser-compat: api.MediaStream.getTracks
---

{{APIRef("Media Capture and Streams")}}

متد **`getTracks()`** از رابط {{domxref("MediaStream")}} یک دنباله (sequence) برمی‌گرداند که تمام اشیاء {{domxref("MediaStreamTrack")}} موجود در [مجموعه‌ی track](https://w3c.github.io/mediacapture-main/#dfn-track-set) این جریان را نشان می‌دهد، بدون در نظر گرفتن {{domxref("MediaStreamTrack.kind")}}.

## نحو

```js-nolint
getTracks()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک آرایه از اشیاء {{domxref("MediaStreamTrack")}}.

## نمونه‌ها

```js
navigator.mediaDevices
  .getUserMedia({ audio: false, video: true })
  .then((mediaStream) => {
    document.querySelector("video").srcObject = mediaStream;
    // Stop the stream after 5 seconds
    setTimeout(() => {
      const tracks = mediaStream.getTracks();
      tracks[0].stop();
    }, 5000);
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}