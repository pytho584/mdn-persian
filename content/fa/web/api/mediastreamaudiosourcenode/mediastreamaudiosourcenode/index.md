---
title: "MediaStreamAudioSourceNode: MediaStreamAudioSourceNode() constructor"
short-title: MediaStreamAudioSourceNode()
slug: Web/API/MediaStreamAudioSourceNode/MediaStreamAudioSourceNode
page-type: web-api-constructor
browser-compat: api.MediaStreamAudioSourceNode.MediaStreamAudioSourceNode
---

{{APIRef("Web Audio API")}}

سازنده **`MediaStreamAudioSourceNode()`** در [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک شیء {{domxref("MediaStreamAudioSourceNode")}} جدید ایجاد و برمی‌گرداند که از اولین آهنگ صوتی یک {{domxref("MediaStream")}} داده شده به عنوان منبع خود استفاده می‌کند.

> [!NOTE]
> راه دیگر برای ایجاد یک `MediaStreamAudioSourceNode` فراخوانی متد {{domxref("AudioContext.createMediaStreamSource()")}} با مشخص کردن استریمی است که می‌خواهید صدا را از آن دریافت کنید.

## Syntax

```js-nolint
new MediaStreamAudioSourceNode(context, options)
```

### Parameters

- `context`
  - : یک {{domxref("AudioContext")}} که زمینه صوتی مورد نظر برای مرتبط‌سازی گره را نشان می‌دهد.
- `options`
  - : یک شیء که ویژگی‌های مورد نظر برای `MediaStreamAudioSourceNode` را تعریف می‌کند:
    - `mediaStream`
      - : یک ویژگی اجباری که {{domxref("MediaStream")}} را مشخص می‌کند که صدا برای گره از آن گرفته می‌شود.

### Return value

یک شیء {{domxref("MediaStreamAudioSourceNode")}} جدید که گره صوتی را نشان می‌دهد و رسانه آن از استریم منبع مشخص شده گرفته می‌شود.

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("MediaStream")}} مشخص شده حاوی هیچ آهنگ صوتی نباشد، پرتاب می‌شود.

## Examples

این مثال از {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} برای دسترسی به دوربین کاربر استفاده می‌کند، سپس یک {{domxref("MediaStreamAudioSourceNode")}} جدید از {{domxref("MediaStream")}} آن ایجاد می‌کند.

```js
// تعریف متغیرها
const audioCtx = new AudioContext();

// بلوک getUserMedia - دریافت استریم
// قرار دادن آن در یک MediaStreamAudioSourceNode
if (navigator.mediaDevices.getUserMedia) {
  navigator.mediaDevices
    .getUserMedia(
      // محدودیت‌ها: صدا و ویدیو برای این برنامه
      {
        audio: true,
        video: false,
      },
    )
    .then((stream) => {
      const options = {
        mediaStream: stream,
      };

      const source = new MediaStreamAudioSourceNode(audioCtx, options);
      source.connect(audioCtx.destination);
    })
    .catch((err) => {
      console.error(`خطای gUM زیر رخ داد: ${err}`);
    });
} else {
  console.log("getUserMedia جدید در مرورگر شما پشتیبانی نمی‌شود!");
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}