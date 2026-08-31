---
title: "AudioBufferSourceNode: detune property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBufferSourceNode/detune"
translated_by: "n8n + AI"
---

---
title: "AudioBufferSourceNode: detune property"
short-title: detune
slug: Web/API/AudioBufferSourceNode/detune
page-type: web-api-instance-property
browser-compat: api.AudioBufferSourceNode.detune
---

{{APIRef("Web Audio API")}}

ویژگی **`detune`** از رابط {{domxref("AudioBufferSourceNode")}} یک {{domxref("AudioParam")}} با [k-rate](/en-US/docs/Web/API/AudioParam#k-rate) است که میزان انحراف نوسان را بر حسب [سانت](https://en.wikipedia.org/wiki/Cent_%28music%29) نشان می‌دهد.

برای مثال، مقادیر 100+ و 100- منبع را به اندازه یک نیم‌پرده بالا یا پایین می‌برند، در حالی که 1200+ و 1200- آن را به اندازه یک اکتاو بالا یا پایین می‌برند.

## مقدار

یک {{domxref("AudioParam")}} با [k-rate](/en-US/docs/Web/API/AudioParam#k-rate) که مقدار آن نشان‌دهنده میزان انحراف نوسان بر حسب [سانت](https://en.wikipedia.org/wiki/Cent_%28music%29) است.

> [!NOTE]
> اگرچه `AudioParam` بازگردانده‌شده فقط‌خواندنی است، اما مقداری که نشان می‌دهد فقط‌خواندنی نیست.

## مثال‌ها

```js
const audioCtx = new AudioContext();

const channelCount = 2;
const frameCount = audioCtx.sampleRate * 2.0; // 2 seconds

const myArrayBuffer = audioCtx.createBuffer(
  channelCount,
  frameCount,
  audioCtx.sampleRate,
);

for (let channel = 0; channel < channelCount; channel++) {
  const nowBuffering = myArrayBuffer.getChannelData(channel);
  for (let i = 0; i < frameCount; i++) {
    nowBuffering[i] = Math.random() * 2 - 1;
  }
}

const source = audioCtx.createBufferSource();
source.buffer = myArrayBuffer;
source.connect(audioCtx.destination);
source.detune.value = 100; // value in cents
source.start();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)