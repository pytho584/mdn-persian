---
title: "AudioBuffer: sampleRate property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBuffer/sampleRate"
translated_by: "n8n + AI"
---

---
title: "AudioBuffer: sampleRate property"
short-title: sampleRate
slug: Web/API/AudioBuffer/sampleRate
page-type: web-api-instance-property
browser-compat: api.AudioBuffer.sampleRate
---

{{ APIRef("Web Audio API") }}

{{domxref("AudioBuffer")}} 接口的 **`sampleRate`** 属性返回一个浮点数，表示缓冲区中存储的 PCM 数据的采样率，单位为每秒样本数。

## 值

一个浮点值，表示缓冲区数据的当前采样率，单位为每秒样本数。

## 示例

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

  console.log(myArrayBuffer.sampleRate);
};
```

## 规格说明

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)