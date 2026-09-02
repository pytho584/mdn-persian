---
title: "MediaElementAudioSourceNode: mediaElement property"
short-title: mediaElement
slug: Web/API/MediaElementAudioSourceNode/mediaElement
page-type: web-api-instance-property
browser-compat: api.MediaElementAudioSourceNode.mediaElement
---

{{APIRef("Web Audio API")}}

ویژگی فقط‌خواندنی **`mediaElement`** در رابط {{domxref("MediaElementAudioSourceNode")}}، عنصر {{domxref("HTMLMediaElement")}} را مشخص می‌کند که حاوی ترک صوتی مبدأ است و این گره صدا را از آن دریافت می‌کند.

این جریان صوتی در زمان ساخت گره تعیین شده است؛ یا با استفاده از سازندهٔ {{domxref("MediaElementAudioSourceNode.MediaElementAudioSourceNode", "MediaElementAudioSourceNode()")}} و یا با استفاده از روش {{domxref("AudioContext.createMediaElementSource()")}}.

## مقدار

یک {{domxref("HTMLMediaElement")}} که عنصرِ حاوی منبع صوتی این گره را نشان می‌دهد.

## مثال‌ها

```js
const audioCtx = new window.AudioContext();
const audioElem = document.querySelector("audio");

let options = {
  mediaElement: audioElem,
};

let source = new MediaElementAudioSourceNode(audioCtx, options);
console.log(source.mediaElement);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}