---
title: "MediaStreamTrackAudioSourceNode: MediaStreamTrackAudioSourceNode() constructor"
short-title: MediaStreamTrackAudioSourceNode()
slug: Web/API/MediaStreamTrackAudioSourceNode/MediaStreamTrackAudioSourceNode
page-type: web-api-constructor
browser-compat: api.MediaStreamTrackAudioSourceNode.MediaStreamTrackAudioSourceNode
---

{{APIRef("Web Audio API")}}

سازندهٔ **`MediaStreamTrackAudioSourceNode()`** در [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)، یک شیء جدید {{domxref("MediaStreamTrackAudioSourceNode")}} می‌سازد و برمی‌گرداند که صدای آن از {{domxref("MediaStreamTrack")}} تعیین‌شده در شیء گزینه‌ها گرفته می‌شود.

روش دیگر برای ایجاد یک `MediaStreamTrackAudioSourceNode`، فراخوانی متد {{domxref("AudioContext.createMediaStreamTrackSource()")}} و تعیین {{domxref("MediaStreamTrack")}} موردنظر برای دریافت صدا است.

## نحو

```js-nolint
new MediaStreamTrackAudioSourceNode(context, options)
```

### پارامترها

- `context`
  - : یک {{domxref("AudioContext")}} که نشان‌دهندهٔ زمینهٔ صوتی‌ای است که می‌خواهید گره به آن مرتبط شود.
- `options`
  - : یک شیء که ویژگی‌های موردنظر برای `MediaStreamTrackAudioSourceNode` را تعریف می‌کند:
    - `mediaStreamTrack`
      - : همان {{domxref("MediaStreamTrack")}}ای است که دادهٔ صوتی خروجی این گره از آن گرفته می‌شود.

### مقدار بازگشتی

یک شیء جدید {{domxref("MediaStreamTrackAudioSourceNode")}} که نمایانگر گرهٔ صوتی است و رسانهٔ آن از تراک رسانه‌ای مشخص‌شده به دست می‌آید.

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر `context` مشخص‌شده یک {{domxref("AudioContext")}} نباشد، صادر می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("MediaStreamTrack")}} مشخص‌شده یک تراک صوتی نباشد (یعنی خاصیت {{domxref("MediaStreamTrack.kind", "kind")}} آن برابر `audio` نباشد)، صادر می‌شود.

## مثال

این مثال با استفاده از {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} به دوربین کاربر دسترسی پیدا می‌کند و سپس یک {{domxref("MediaStreamAudioSourceNode")}} جدید از اولین تراک صوتی ارائه‌شده توسط دستگاه می‌سازد.

```js
const audioCtx = new AudioContext();

if (navigator.mediaDevices.getUserMedia) {
  navigator.mediaDevices
    .getUserMedia({
      audio: true,
      video: false,
    })
    .then((stream) => {
      const options = {
        mediaStreamTrack: stream.getAudioTracks()[0],
      };

      const source = new MediaStreamTrackAudioSourceNode(audioCtx, options);
      source.connect(audioCtx.destination);
    })
    .catch((err) => {
      console.error(`The following gUM error occurred: ${err}`);
    });
} else {
  console.log("new getUserMedia not supported on your browser!");
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}