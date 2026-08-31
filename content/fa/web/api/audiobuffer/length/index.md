---
title: "AudioBuffer: length property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBuffer/length"
translated_by: "n8n + AI"
---

---
title: "AudioBuffer: length property"
short-title: length
slug: Web/API/AudioBuffer/length
page-type: web-api-instance-property
browser-compat: api.AudioBuffer.length
---

{{ APIRef("Web Audio API") }}

ویژگی **`length`** از رابط {{ domxref("AudioBuffer") }} یک عدد صحیح را برمی‌گرداند که طول داده‌های PCM ذخیره شده در بافر را بر حسب نمونه-فریم (sample-frames) نشان می‌دهد.

## مقدار

یک عدد صحیح.

## نمونه‌ها

```js
// Stereo
const channels = 2;

// Create an empty two second stereo buffer at the
// sample rate of the AudioContext
const frameCount = audioCtx.sampleRate * 2.0;
const myArrayBuffer = audioCtx.createBuffer(2, frameCount, audioCtx.sampleRate);

button.onclick = () => {
  // Fill the buffer with white noise;
  // just random values between -1.0 and 1.0
  for (let channel = 0; channel < channels; channel++) {
    // This gives us the actual ArrayBuffer that contains the data
    const nowBuffering = myArrayBuffer.getChannelData(channel);
    for (let i = 0; i < frameCount; i++) {
      // Math.random() is in [0; 1.0]
      // audio needs to be in [-1.0; 1.0]
      nowBuffering[i] = Math.random() * 2 - 1;
    }
  }

  console.log(myArrayBuffer.length);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)